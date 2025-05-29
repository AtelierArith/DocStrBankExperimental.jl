```
BlochMessiah <: Factorization
```

Matrix factorization type of the Bloch-Messiah/Euler decomposition of a symplectic matrix `S`. This is the return type of [`blochmessiah(_)`](@ref), the corresponding matrix factorization function.

If `F::BlochMessiah` is the factorization object, `O`, `values` and Q`can be obtained via`F.O`,`F.values`, and`F.Q`.

Iterating the decomposition produces the components `O`, `values`, and `Q`, in that order.

# Examples

```
julia> S = Symplectic(BlockForm(1), [1. 1.; 0. 1.])
2×2 Symplectic{BlockForm{Int64}, Float64, Matrix{Float64}}:
 1.0  1.0
 0.0  1.0

julia> issymplectic(S)
true

julia> F = blochmessiah(S)
BlochMessiah{Float64, Symplectic{BlockForm{Int64}, Float64, Matrix{Float64}}, Vector{Float64}}
O factor:
2×2 Symplectic{BlockForm{Int64}, Float64, Matrix{Float64}}:
 0.850651  -0.525731
 0.525731   0.850651
values:
1-element Vector{Float64}:
 1.618033988749895
Q factor:
2×2 Symplectic{BlockForm{Int64}, Float64, Matrix{Float64}}:
  0.525731  0.850651
 -0.850651  0.525731

julia> isapprox(S, F.O * Diagonal(vcat(F.values, F.values .^ (-1))) * F.Q, atol = 1e-10)
true

julia> issymplectic(F.O, atol = 1e-10) && issymplectic(F.Q, atol = 1e-10)
true

julia> O, values, Q = F; # destructuring via iteration

julia> O == F.O && values == F.values && Q == F.Q
true
```
