```
connect!(client::WSClient; max_retries::Int = MAX_RETRIES,
    retry_delay::Real = RETRY_DELAY,  timeout::Real = CONNECTION_TIMEOUT, verbose::Bool = false)
```

Connect to Chrome DevTools Protocol WebSocket endpoint. Returns the connected client.

# Arguments

  * `max_retries::Int`: The maximum number of retries to establish the connection.
  * `retry_delay::Real`: The delay between retries in seconds.
  * `timeout::Real`: The timeout for the connection in seconds.
  * `verbose::Bool`: Whether to print verbose debug information.
