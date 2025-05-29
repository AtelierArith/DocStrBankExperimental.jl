```
fetch_tles(fetcher::CelestrakTleFetcher; kwargs...) -> Union{Nothing, Vector{TLE}}
```

Fetch TLEs from the Celestrak using `fetch` with the parameters in `kwargs...`.

This function returns a `Vector{TLE}` with the fetched TLEs. If an error is found, it returns `nothing`.

# Keywords

  * `international_designator::Union{Nothing, AbstractString}`: International designator using   the Celestrak format `YYYY-NNN`, where `YYYY` is the launch year, and the `NNN` is the   launch number. (**Default**: `nothing`)
  * `satellite_number::Union{Nothing, Number}`: Satellite catalog number (NORAD).   (**Default** = `nothing`)
  * `satellite_name::Union{Nothing, AbstractString}`: Satellite name. Notice that the system   will search for all satellites whose name contains this string. (**Default**: `nothing`)

!!! note
    Only one search parameter is supported. If more than one is given, the precedence is: 1) `satellite_number`; 2) `international_designator`; and 3) and `satellite_name`.


!!! note
    If no search parameter is provided, the function throws an error.

