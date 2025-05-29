```
send_cdp(
    client::WSClient, method::String, params::Dict = Dict();
    increment_id::Bool = true, timeout::Real = CONNECTION_TIMEOUT)
```

Send a Chrome DevTools Protocol message and wait for the response.

# Arguments

  * `client::WSClient`: The WebSocket client to use
  * `method::String`: The CDP method to call (e.g., "Page.navigate")
  * `params::Dict`: Parameters for the CDP method (default: empty Dict)
  * `increment_id::Bool`: Whether to increment the message ID counter (default: true)
  * `timeout::Real`: The timeout for the response in seconds (default: CONNECTION_TIMEOUT)

# Returns

  * `Dict`: The CDP response message

# Throws

  * `TimeoutError`: If response times out
