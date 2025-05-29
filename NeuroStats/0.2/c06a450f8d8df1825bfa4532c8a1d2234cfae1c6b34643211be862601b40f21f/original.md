```
summary(x, y)
```

Return summary statistics.

# Arguments

  * `x::AbstractVector`
  * `y::AbstractVector`
  * `g1::String="1"`: group 1 name
  * `g2::String="2"`: group 2 name

# Returns

Named tuple containing:

  * `mm1::Float64`: mean
  * `mm2::Float64`: mean
  * `v1::Float64`: variance
  * `v2::Float64`: variance
  * `s1::Float64`: standard deviation
  * `s2::Float64`: standard deviation
  * `me1::Float64`: median
  * `me2::Float64`: median
  * `mo1::Float64`: mode
  * `mo2::Float64`: mode
