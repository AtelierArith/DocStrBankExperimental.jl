```
Varimax()
```

The *Varimax* rotation criterion.

## Details

The *Varimax* is an orthogonal rotation method that maximizes the column variances of the loading matrix $Λ ∈ ℝ^{p × k}$:

$$
Q(Λ) = -\frac{p}{4} ∑_{j=1}^{k} \mathrm{Var}_i(Λ_{i, j}).
$$

It is a special case of the [`Oblimin`](@ref) rotation criterion with parameter `gamma = 1`.

## Examples

### Setting up the criterion

```jldoctest
julia> Varimax()
Varimax()
```

### Testing equivalence of Varimax and Oblimin

```jldoctest; filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2"
julia> L = [
           0.830 -0.396
           0.818 -0.469
           0.777 -0.470
           0.798 -0.401
           0.786  0.500
           0.672  0.458
           0.594  0.444
           0.647  0.333
       ];

julia> L_varimax = rotate(L, Varimax());

julia> L_oblimin = rotate(L, Oblimin(gamma = 1, orthogonal = true));

julia> loadings(L_varimax) ≈ loadings(L_oblimin)
true
```
