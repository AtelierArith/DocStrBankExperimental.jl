```
with_retry(f::Function; max_retries::Int = MAX_RETRIES, retry_delay::Real = RETRY_DELAY, verbose::Bool = false)
```

Executes the function `f` with retry logic. It will attempt to execute `f` up to `max_retries` times, waiting `retry_delay` seconds between attempts.

# Arguments

  * `f::Function`: The function to execute with retries.
  * `max_retries::Int`: The maximum number of retries.
  * `retry_delay::Real`: The delay between retries in seconds.
  * `verbose::Bool`: Whether to print verbose debug information.

# Returns

  * The result of executing `f` if successful.

# Throws

  * The last exception encountered if all retries fail.
