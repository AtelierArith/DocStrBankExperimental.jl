```
receive(rp::RedPitaya, ch::Channel)
```

Receive a String from the RedPitaya command socket. Reads until a whole line is received and puts it in the supplied channel `ch`.
