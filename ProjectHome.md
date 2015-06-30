# Simple Winsock Wrapper #
SWW is a very simple and easy to use Winsock wrapper for text based communication.

Useful for text based protocols like HTTP, POP3, IMAP, SMTP or IRC. Also useful for beginners to quickly make e.g. P2P chat programs.

## Examples ##
**A simple blocking server**
```
// Create an instance of the server class
sww::Server server;
// Bind to port 23 (Telnet)
server.Bind(23);
// Listen until connection attempt
while (server.Listen() != SOCKET_ERROR);
// Accept the socket and get the client handle
sww::Client client = server.Accept();
// Send our little welcome message
client.Send("Thank you Mario! But our princess is in another castle!");
// Drop the client
client.Drop();
```

**A simple Telnet client**
```
// Create and instance of the client class
sww::Client client;
// Connect to the server on port 23 (Telnet)
client.Connect("127.0.0.1", 23);
// Recieve
std::string text = client.Recieve();
// Print what the server sent us
std::cout << "Recv: " << text << std::endl;
// Disconnect
client.Disconnect();
```