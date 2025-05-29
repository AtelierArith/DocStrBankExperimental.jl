```
gamereviews(id::Integer; kwargs...)
```

Scrape all reviews for a game

# Keyword arguments

  * `pagesize::Integer`: Number of reviews per page request. Defaults to API maximum 100.
  * `waittime::Real`: Wait time between page requests in seconds. Defaults to `2.0f0`.
