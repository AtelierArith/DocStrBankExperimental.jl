```
rsp = request(gw, msg[, timeout])
```

Send a request via the gateway to the specified agent, and wait for a response. The response is returned. The `recipient` field of the request message (`msg`) must be populated with an agentID. The timeout is specified in milliseconds, and defaults to 1 second if unspecified.
