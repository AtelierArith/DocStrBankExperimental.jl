```
enum_linear_regions_rat(f::TropicalPuiseuxPoly, g::TropicalPuiseuxPoly, verbose)
```

トロピカル・プイセウス有理関数 f/g の線形領域を計算します。入力: トロピカル・プイセウス多項式 f と g 出力: 多面体/多面体の配列で表される f/g の線形領域を含む配列。

# 例

f = max(x, y) および g = max(x+y, x+2y) の場合の f/g の線形領域を列挙します。

```jldoctest
julia> f = TropicalPuiseuxPoly(Dict([1, 0] => 0, [0, 1] => 0), [[1, 0], [0, 1]]);

julia> g = TropicalPuiseuxPoly(Dict([1, 1] => 0, [1, 2] => 0), [[1, 1], [1, 2]]);

julia> enum_linear_regions_rat(f, g)
4-element Vector{Any}:
 Polyhedron in ambient dimension 2 with Float64 type coefficients
 Polyhedron in ambient dimension 2 with Float64 type coefficients
 Polyhedron in ambient dimension 2 with Float64 type coefficients
 Polyhedron in ambient dimension 2 with Float64 type coefficients
```
