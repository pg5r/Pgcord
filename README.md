# PGCORD
## 1.0

A lightweight encrypted TCP chat system built in Python.

---

## Overview

PGCORD is a client–server messaging system that allows multiple users to communicate over a TCP connection with symmetric encryption using Fernet.  
The system is designed for local networks and testing environments, focusing on simplicity, real-time communication, and encrypted message exchange.

It consists of two components:

- **Server**: Handles connections, authentication, and message relay  
- **Client**: GUI-based chat application using Tkinter

---

## Architecture

### Server
The server acts as a central relay between connected clients.

Responsibilities:
- Accept incoming TCP connections
- Manage multiple clients concurrently using threads
- Generate and distribute a single encryption key per session
- Authenticate clients before allowing communication
- Broadcast encrypted messages to all connected clients

Connection flow:
1. Client connects to server
2. Client sends authentication request
3. Server validates key
4. Server assigns a session ID (PID)
5. Encrypted messaging begins

---

### Client
The client provides a graphical interface for sending and receiving messages.

Capabilities:
- Connect to a remote or local server
- Authenticate using a shared cipher key
- Send encrypted messages
- Receive and decrypt messages in real time
- Display chat history in a scrollable interface

---

## Security

PGCORD uses symmetric encryption based on Fernet (AES).

- Each session uses a single shared key
- All messages are encrypted before transmission
- Messages are decrypted only on authorized clients

# PgCord Server - Commands

Each running server is identified by a PID.

---

## Start Server
serve [port|default] [local|public] [servername:required]

- port → any valid port number (example: 5000) 
- default → uses port 125  

### Bind types:
- local → 127.0.0.1 (local machine only)  
- public → 0.0.0.0 (accessible on network [Including Lan])

---

## Show Running Servers
showpids  
Displays all active server PIDs.

---

## Stop Server
unserve [pid]  
Stops the server with the specified PID.

## ⚠ WARNING

Running a global/public server from a home network usually will not work because of NAT, firewalls, or blocked ports.

For public connections, use a VPS or hosting with a public IP.

Home devices can still communicate normally inside the same local network (LAN).

You Can use ZeroTier if you want a server in your device

