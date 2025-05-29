```
timezone_at(latitude, longitude)
```

Get any uniquely applicable timezone at the given `latitude` and `longitude`.

```jldoctest
julia> timezone_at(52.5061, 13.358)
Europe/Berlin (UTC+1/UTC+2)
```

See additional note on docstring for [`timezone_at`](@ref) regarding the version of tzdata that will be used.

# Returns

  * a `TimeZone` instance if `latitude` and `longitude` correspond to a unqiue timezone.
  * `nothing` if no timezone is found.

An exception is raised if multiple timezones correspond to this location - use [`timezones_at`](@ref) to obtain all the matches.
