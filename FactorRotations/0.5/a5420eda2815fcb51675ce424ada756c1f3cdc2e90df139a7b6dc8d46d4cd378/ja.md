```
Quartimax()
```

*Quartimax* 回転基準。

## 詳細

*Quartimax* 基準は、パラメータ `gamma = 0` の [`Oblimin`](@ref) 回転基準の特別なケースです。

## 例

### 基準の設定

```jldoctest
julia> Quartimax()
Quartimax()
```

### Quartimax と Oblimin の同等性のテスト

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

julia> L_quartimax = rotate(L, Quartimax());

julia> L_oblimin = rotate(L, Oblimin(gamma = 0, orthogonal = true));

julia> loadings(L_quartimax) ≈ loadings(L_oblimin)
true
```
