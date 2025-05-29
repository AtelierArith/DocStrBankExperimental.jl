```
dim_M(n, d, m)
```

The dimension of the moduli space of stable rational map to the projective space of dimension `n`, of degree `d` with `m` marks.

# Arguments

  * `n::Int64`: the dimension of the projective space.
  * `d::Int64`: the degree of the stable maps.
  * `m::Int64`: the number of marks.

# Example

```julia-repl
julia> dim_M(2,2,5)
10
```
