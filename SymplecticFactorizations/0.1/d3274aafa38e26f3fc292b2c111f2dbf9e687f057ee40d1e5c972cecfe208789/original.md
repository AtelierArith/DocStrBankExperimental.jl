```
Williamson <: Factorization
```

Matrix factorization type of the williamson decomposition of a positive-definite matrix `V`. This is the return type of [`williamson(_)`](@ref), the corresponding matrix factorization function.

If `F::Williamson` is the factorization object, `S` and `spectrum` can be obtained via `F.S` and `F.spectrum`.

Iterating the decomposition produces the components `S` and `spectrum`.

# Examples

```
julia> V = [7. 2.; 2. 1.]
2×2 Matrix{Float64}:
 7.0  2.0
 2.0  1.0

julia> isposdef(V)
true

julia> F = williamson(BlockForm(1), V)
Williamson{Float64, Matrix{Float64}, Vector{Float64}}
S factor:
2×2 Matrix{Float64}:
 0.448828  -1.95959
 0.61311   -0.448828
symplectic spectrum:
1-element Vector{Float64}:
 1.7320508075688772

julia> isapprox(F.S * V * F.S', Diagonal(repeat(F.spectrum, 2)))
true

julia> S, spectrum = F; # destructuring via iteration

julia> S == F.S && spectrum == F.spectrum
true
```
