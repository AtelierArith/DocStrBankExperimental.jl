```
Polar <: Factorization
```

Matrix factorization type of the polar decomposition of a symplectic matrix `S`. This is the return type of [`polar(_)`](@ref), the corresponding matrix factorization function.

If `F::Polar` is the factorization object, `O` and `P` can be obtained via `F.O` and `F.P`, such that `S = O * P`.

Iterating the decomposition produces the components `O` and `P`.

# Examples

```jldoctest
julia> S = [1. 1.; 0. 1.]
2×2 Matrix{Float64}:
 1.0  1.0
 0.0  1.0

julia> issymplectic(BlockForm(1), S)
true

julia> F = polar(S)
Polar{Float64, Matrix{Float64}, Matrix{Float64}}
O factor:
2×2 Matrix{Float64}:
  0.894427  0.447214
 -0.447214  0.894427
P factor:
2×2 Matrix{Float64}:
 0.894427  0.447214
 0.447214  1.34164

julia> isapprox(F.O * F.P, S)
true

julia> O, P = F; # destructuring via iteration

julia> O == F.O && P == F.P
true
```
