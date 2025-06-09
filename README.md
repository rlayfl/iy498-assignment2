# iy498-assignment2

CREATE DATABASE <YourDBName>;

USE <YourDBName>;

-- Drop existing tables if they exist
DROP TABLE IF EXISTS Equipment_Purchased;
DROP TABLE IF EXISTS Orders;
DROP TABLE IF EXISTS Equipment;
DROP TABLE IF EXISTS Clients;

-- 1. Create Tables
CREATE TABLE Clients (
    ClientId VARCHAR(10) PRIMARY KEY,
    Name VARCHAR(100),
    Address VARCHAR(255),
    DateOfBirth DATE
);

CREATE TABLE Equipment (
    EquipCode VARCHAR(10) PRIMARY KEY,
    EquipDescription VARCHAR(100),
    Price DECIMAL(10, 2)
);

CREATE TABLE Orders (
    OrderNo VARCHAR(10) PRIMARY KEY,
    OrderDate DATE,
    ClientId VARCHAR(10),
    FOREIGN KEY (ClientId) REFERENCES Clients(ClientId)
);

CREATE TABLE Equipment_Purchased (
    EquipCode VARCHAR(10),
    OrderNo VARCHAR(10),
    Quantity INT,
    PRIMARY KEY (EquipCode, OrderNo),
    FOREIGN KEY (EquipCode) REFERENCES Equipment(EquipCode),
    FOREIGN KEY (OrderNo) REFERENCES Orders(OrderNo)
);

-- Insert data into Clients
INSERT INTO Clients (ClientId, Name, Address, DateOfBirth) VALUES 
('C001', 'Emily Thompson', '12 High Street, Cambridge', '1995-03-22'),
('C002', 'Jack Wilson', '88 London Road, Manchester', '1987-07-11'),
('C003', 'Sophie Patel', '7 Queen’s Avenue, Birmingham', '1992-01-09'),
('C004', 'Harry Clark', '34 The Crescent, Oxford', '1984-12-17'),
('C005', 'Olivia Davies', '19 Market Place, York', '1990-06-05'),
('C006', 'Charlie Taylor', '45 Church Lane, Bath', '1993-08-28'),
('C007', 'Amelia Wright', '3 Station Road, Brighton', '1996-04-14'),
('C008', 'George Harris', '67 Victoria Street, Liverpool', '1981-10-02');

-- Insert data into Equipment
INSERT INTO Equipment (EquipCode, EquipDescription, Price) VALUES 
('E001', 'Treadmill - Compact UK Model', 725.00),
('E002', 'Spin Bike - Home Edition', 499.99),
('E003', 'Rowing Machine - Foldable', 599.50),
('E004', 'Cross Trainer', 849.99),
('E005', 'Yoga Set (Mat, Blocks, Strap)', 68.00),
('E006', 'Kettlebell Set - 4kg to 24kg', 130.00),
('E007', 'Resistance Band Kit', 35.00),
('E008', 'Boxing Bag - Wall Mount', 220.00);

-- Insert data into Orders
INSERT INTO Orders (OrderNo, OrderDate, ClientId) VALUES 
('O001', '2025-01-15', 'C001'),
('O002', '2025-02-03', 'C002'),
('O003', '2025-02-20', 'C003'),
('O004', '2025-03-10', 'C004'),
('O005', '2025-04-07', 'C001'),
('O006', '2025-04-25', 'C005'),
('O007', '2025-05-01', 'C006'),
('O008', '2025-05-12', 'C007'),
('O009', '2025-06-02', 'C008');

-- Insert data into Equipment_Purchased
INSERT INTO Equipment_Purchased (EquipCode, OrderNo, Quantity) VALUES 
('E001', 'O001', 1),
('E005', 'O001', 2),
('E002', 'O002', 1),
('E007', 'O002', 1),
('E003', 'O003', 1),
('E006', 'O004', 1),
('E004', 'O005', 1),
('E008', 'O006', 1),
('E005', 'O006', 1),
('E007', 'O007', 2),
('E006', 'O008', 1),
('E001', 'O009', 1),
('E003', 'O009', 1);
