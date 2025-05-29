```
enum_linear_regions(f::TropicalPuiseuxPoly)
```

fの指数と同じ集合でインデックス付けされたタプル (poly, bool) の配列を出力します。タプル要素 poly は指数に対応する線形領域であり、bool はこの領域が空でない場合にtrueになります。

# 例

f = max(x, y) の線形領域を列挙します。

```jldoctest
julia> f = TropicalPuiseuxPoly(Dict([1, 0] => 0, [0, 1] => 0), [[1, 0], [0, 1]]);

julia> enum_linear_regions(f)
2-element Vector{Any}:
 (Polyhedron in ambient dimension 2 with Float64 type coefficients, true)
 (Polyhedron in ambient dimension 2 with Float64 type coefficients, true)
```
