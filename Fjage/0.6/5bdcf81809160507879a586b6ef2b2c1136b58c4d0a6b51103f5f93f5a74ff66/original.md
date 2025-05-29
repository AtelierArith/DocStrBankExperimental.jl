```
request(a::Agent, msg::Message)
request(a::Agent, msg::Message, timeout::Int)
```

Send a request and wait for a response. If a timeout is specified, the call blocks for at most `timeout` milliseconds. If no timeout is specified, a system default is used. Returns the response message or `nothing` if no response received.
