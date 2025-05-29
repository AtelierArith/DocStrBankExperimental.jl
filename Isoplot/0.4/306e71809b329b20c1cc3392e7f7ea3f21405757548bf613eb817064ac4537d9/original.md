```julia
(a,b) = lsqfit(x::AbstractVector, y::AbstractVector)
```

Returns the coefficients for a simple linear least-squares regression of the form `y = a + bx`

### Examples

```
julia> a, b = lsqfit(1:10, 1:10)
2-element Vector{Float64}:
 -1.19542133983862e-15
  1.0

julia> isapprox(a, 0, atol = 1e-12)
true

julia> isapprox(b, 1, atol = 1e-12)
true
```
