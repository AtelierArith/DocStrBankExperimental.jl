```
rewind(r, index)
```

Rewind a rational approximation to a state encountered during an iteration.

# Arguments

  * `r::Approximation}`: the approximation to rewind
  * `index::Integer`: the iteration number to rewind to

# Returns

  * the rational function of the specified index (same type as input)

# Examples

```jldoctest
julia> r = approximate(x -> cos(20x), unit_interval)
Barycentric{Float64, Float64} rational interpolant of type (24, 24) on the domain: Path{Float64} with 1 curve

julia> rewind(r, 10)
Barycentric{Float64, Float64} rational interpolant of type (10, 10) on the domain: Path{Float64} with 1 curve
```
