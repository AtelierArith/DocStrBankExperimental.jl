```
fetch_tles(fetcher::T; kwargs...) -> Vector{TLE}
```

Fetch TLEs using `fetcher`.

The keywords `kwargs...` are used to customize the search. It depends on the fetcher type `T`.
