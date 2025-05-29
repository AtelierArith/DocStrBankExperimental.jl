```
Biquartimax()
```

The *Biquartimax* rotation method.

## Details

The *Biquartimax* rotation method is a special case of the [`Oblimin`](@ref) rotation with parameters `gamma = 0.5` and `orthogonal = true`.

## Examples

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

julia> L_biquartimax = rotate(L, Biquartimax());

julia> L_oblimin = rotate(L, Oblimin(gamma = 0.5, orthogonal = true));

julia> loadings(L_biquartimax) ≈ loadings(L_oblimin)
true
```
