```
polar(S::AbstractMatrix) -> Polar
polar(S::Symplectic) -> Polar
```

Compute the polar decomposition of a symplectic matrix `S` and return a `Polar` object.

`O` and `P` can be obtained from the factorization `F` via `F.O` and `F.P`, such that `S = O * P`. For the symplectic polar decomposition case, `O` is an orthogonal symplectic matrix and `P` is a positive-definite symmetric symplectic matrix.

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
