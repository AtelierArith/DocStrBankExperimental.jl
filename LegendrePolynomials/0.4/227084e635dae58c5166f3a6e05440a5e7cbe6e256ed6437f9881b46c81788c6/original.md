```
collectPl!(v::AbstractVector, x; [lmin::Integer = 0], [lmax::Integer = length(v) - 1 + lmin], [kwargs...])
```

Compute the Legendre Polynomials $P_\ell(x)$ for the argument `x` and degrees `l = lmin:lmax`, and store them in `v`.

At output `v[firstindex(v) + l] == Pl(x, l; kwargs...)`.

# Optional keyword arguments

  * `norm`: The normalization used in the function. Possible   options are `Val(:standard)` (default) and `Val(:normalized)`.   The functions obtained with `norm = Val(:normalized)` have an L2 norm of $1$.

# Examples

```jldoctest
julia> v = zeros(4);

julia> collectPl!(v, 0.5);

julia> all(zip(0:3, v)) do (l, vl); vl ≈ Pl(0.5, l); end
true

julia> collectPl!(v, 0.5, norm = Val(:normalized));

julia> all(zip(0:3, v)) do (l,vl); vl ≈ Pl(0.5, l, norm = Val(:normalized)); end
true

julia> v = zeros(0:4);

julia> collectPl!(v, 0.5, lmax = 3) # only l from 0 to 3 are populated
5-element OffsetArray(::Vector{Float64}, 0:4) with eltype Float64 with indices 0:4:
  1.0
  0.5
 -0.125
 -0.4375
  0.0
```
