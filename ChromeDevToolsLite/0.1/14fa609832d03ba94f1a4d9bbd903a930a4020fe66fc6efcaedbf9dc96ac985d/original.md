```
ensure_browser_available(
    endpoint::String;
    max_retries::Int = MAX_RETRIES,
    retry_delay::Real = RETRY_DELAY,
    verbose::Bool = false
```

)

Checks if Chrome is running in debug mode on the specified endpoint. Retries up to `max_retries` times with specified `retry_delay` between attempts. Returns `true` if Chrome is responding on the debug port.

# Arguments

  * `endpoint::String`: The URL of the Chrome debugging endpoint. Eg, `http://localhost:9222`.
  * `max_retries::Int`: The maximum number of retries to check for Chrome.
  * `retry_delay::Real`: The delay between retries in seconds.
  * `verbose::Bool`: Whether to print verbose debug information.
