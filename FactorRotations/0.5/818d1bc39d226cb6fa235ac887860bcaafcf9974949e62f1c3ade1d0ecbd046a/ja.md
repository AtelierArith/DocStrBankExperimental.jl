```
Oblimax(; orthogonal = false)
```

*Oblimax*回転法。

## キーワード引数

  * `orthogonal`: `orthogonal = true`の場合は直交回転が行われ、それ以外の場合は斜交回転が行われます。（デフォルト: `false`）

## 詳細

*Oblimax*回転法は、直交回転に対して[`Quartimax`](@ref)と同等です。

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

julia> L_oblimax = rotate(L, Oblimax(orthogonal = true));

julia> L_quartimax = rotate(L, Quartimax());

julia> isapprox(loadings(L_oblimax), loadings(L_quartimax), atol = 1e-6)
true
```
