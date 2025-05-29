```
check(r; quiet=false, prenodes=false)
```

Check the accuracy of a rational approximation `r` on its domain. Returns the test points and the error at those points.

# Arguments

  * `r::Approximation`: rational approximation

# Keywords

  * `quiet::Bool=false`: suppress @info output
  * `prenodes::Bool=false`: return prenodes of the approximation as well

# Returns

  * `τ::Vector`: test points
  * `err::Vector`: error at test points

See also [`approximate`](@ref).
