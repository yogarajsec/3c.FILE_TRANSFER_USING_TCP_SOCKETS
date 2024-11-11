# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## Name: Yogaraj S
## Reg: 212223040248

## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
  ## client:
  ```
  import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    while True:
        print('receiving data...')
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
    f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
  ```
  ## server:
  ```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename='yogi.txt'
    f = open(filename,'rb')
    l = f.read(1024)
    while (l):
        conn.send(l)
        print('Sent ',repr(l))
        l = f.read(1024)
    f.close()
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
```
## OUPUT
![Screenshot 2024-11-11 205506](https://github.com/user-attachments/assets/9516aa6d-9cbe-48f4-9b7e-2f55466a5f63)
![Screenshot 2024-11-11 205521](https://github.com/user-attachments/assets/548af4f5-db37-4ee0-bed2-6209bbb00c6b)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
