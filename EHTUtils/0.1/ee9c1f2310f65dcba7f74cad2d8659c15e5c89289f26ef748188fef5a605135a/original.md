```
mjd2hour(mjd, refmjd=nothing)
```

Convert a given array of mjd into utc hours.

  * `mjd::AbstractArray`: the input array of the modified Julian dates.
  * `refmjd::Number`: the reference date. Default to `floor(minimum(mjd))`.
