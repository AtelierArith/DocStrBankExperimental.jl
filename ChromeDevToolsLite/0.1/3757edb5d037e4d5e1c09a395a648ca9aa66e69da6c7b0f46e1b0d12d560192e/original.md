```
connect_browser(
    endpoint::String = "http://localhost:9222";
    max_retries::Int = MAX_RETRIES,
    retry_delay::Real = RETRY_DELAY,
    timeout::Real = CONNECTION_TIMEOUT,
    verbose::Bool = false
```

)

Connects to Chrome browser at the given debugging endpoint with enhanced error handling. Returns a WSClient connected to a new page.

# Arguments

  * `endpoint::String`: The URL of the Chrome debugging endpoint. Eg, `http://localhost:9222`.
  * `max_retries::Int`: The maximum number of retries to check for Chrome.
  * `retry_delay::Real`: The delay between retries in seconds.
  * `timeout::Real`: The timeout for the connection in seconds.
  * `verbose::Bool`: Whether to print verbose debug information.
