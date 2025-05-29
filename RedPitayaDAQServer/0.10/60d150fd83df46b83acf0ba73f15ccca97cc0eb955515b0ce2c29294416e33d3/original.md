```
receive(rp::RedPitaya, timeout::Number)
```

Receive a string from the RedPitaya command socket. Reads until a whole line is received or timeout seconds passed. In the latter case an error is thrown.
