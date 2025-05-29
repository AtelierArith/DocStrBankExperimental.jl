```
Biquartimax()
```

*Biquartimax*回転法。

## 詳細

*Biquartimax*回転法は、パラメータ`gamma = 0.5`および`orthogonal = true`を持つ[`Oblimin`](@ref)回転の特別なケースです。

## 例

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
