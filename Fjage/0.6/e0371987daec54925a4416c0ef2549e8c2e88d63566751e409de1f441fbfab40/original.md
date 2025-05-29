```
msg = Message([perf])
msg = Message(inreplyto[, perf])
```

Create a message with just a performative (`perf`) and no data. If the performative is not specified, it defaults to INFORM. If the inreplyto is specified, the message `inReplyTo` and `recipient` fields are set accordingly.
