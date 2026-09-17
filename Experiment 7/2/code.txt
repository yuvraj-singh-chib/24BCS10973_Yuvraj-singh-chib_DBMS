-- Experiment 7

-- Create Orders Table
CREATE TABLE Orders (
    Order_ID NUMBER PRIMARY KEY,
    Customer_Name VARCHAR2(100),
    Amount NUMBER(10,2)
);

-- Insert Sample Data
INSERT INTO Orders VALUES (101, 'Rahul', 12000);
INSERT INTO Orders VALUES (102, 'Amit', 8000);
INSERT INTO Orders VALUES (103, 'Priya', 15000);
INSERT INTO Orders VALUES (104, 'Neha', 9500);
INSERT INTO Orders VALUES (105, 'Rohit', 20000);

COMMIT;

-- Enable Output
SET SERVEROUTPUT ON;

-- PL/SQL Cursor Loop
BEGIN
    FOR rec IN (
        SELECT Order_ID, Customer_Name, Amount
        FROM Orders
    )
    LOOP
        IF rec.Amount > 10000 THEN
            DBMS_OUTPUT.PUT_LINE(
                'Order ID: ' || rec.Order_ID ||
                ', Customer: ' || rec.Customer_Name ||
                ', Amount: ' || rec.Amount ||
                ' --> High Value'
            );
        END IF;
    END LOOP;
END;
/