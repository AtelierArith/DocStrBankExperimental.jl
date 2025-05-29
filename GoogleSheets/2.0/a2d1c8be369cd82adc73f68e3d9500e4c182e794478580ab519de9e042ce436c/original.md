```
sheets_client(scopes::Union{AuthScope,Array{AuthScope,1}}; 
    rate_limiter_read::AbstractRateLimiter=default_rate_limiter_read, 
    rate_limiter_write::AbstractRateLimiter=default_rate_limiter_write)::GoogleSheetsClient
```

Creates a client for accessing Google Sheets.

# Arguments

  * `scopes::Union{AuthScope,Array{AuthScope,1}}`: authorization scopes.
  * `rate_limiter_read::AbstractRateLimiter=default_rate_limiter_read`: rate limiter for reading.
  * `rate_limiter_write::AbstractRateLimiter=default_rate_limiter_write`: rate limiter for writing.
