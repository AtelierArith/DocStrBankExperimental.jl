```
grubbs(x; <keyword arguments>)
```

Perform Grubbs test for outlier.

# Arguments

  * `x::AbstractVector`
  * `alpha::Float64=0.95`
  * `t::Int64=0`: test type:

      * `-1`: test whether the minimum value is an outlier
      * `0`: two-tiled test
      * `1`: test whether the maximum value is an outlier

# Returns

  * `g::Bool`: true: outlier exists, false: there is no outlier
