```
rsp = request(aid, msg[, timeout])
```

Send a request via the gateway to the specified agent, and wait for a response. The response is returned. The agentID (`aid`) specified must be an "owned" agentID obtained from the `agent(gw, name)` function or returned by the `agentforservice(gw, service)` function. The timeout is specified in milliseconds, and defaults to 1 second if unspecified.
