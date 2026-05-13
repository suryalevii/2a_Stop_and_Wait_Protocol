# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### Server
~~~
import socket

# Create socket
s = socket.socket()

# Bind IP and port
s.bind(('localhost', 8000))

# Listen for client connections
s.listen(5)

print("Server waiting for connection...")

# Accept client connection
c, addr = s.accept()

print("Connected to:", addr)

while True:
    # Take input from server user
    data = input("Enter a data: ")

    # Send data to client
    c.send(data.encode())

    # Receive acknowledgement
    ack = c.recv(1024).decode()

    if ack:
        print(ack)
    else:
        c.close()
        break

~~~
### Client
~~~
import socket

# Create socket
s = socket.socket()

# Connect to server
s.connect(('localhost', 8000))

while True:
    # Receive message from server
    print(s.recv(1024).decode())

    # Send acknowledgement
    s.send("Acknowledgement Received".encode())

~~~
## OUTPUT
<img width="1920" height="1080" alt="Screenshot 2026-05-13 132603" src="https://github.com/user-attachments/assets/d38a1a2d-e27b-4b3d-8829-8b6d79c6cd09" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
