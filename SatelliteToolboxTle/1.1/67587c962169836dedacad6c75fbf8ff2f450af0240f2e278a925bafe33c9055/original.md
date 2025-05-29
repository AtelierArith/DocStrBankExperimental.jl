```
create_tle_fetcher(::Type{CelestrakTleFetcher}; kwargs...) -> CelestrakTleFetcher
```

Create a TLE fetcher from Celestrak service.

# Keywords

  * `url::String`: Default PHP webpage address that will be used to perform the queries. (**Default**: "https://celestrak.org/NORAD/elements/gp.php")
