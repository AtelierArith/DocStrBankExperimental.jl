```
polyhedron(f::TropicalPuiseuxPoly, i::Int)
```

fがfのi番目の単項式に対応する線形写像によって与えられる点のポリヘドロンを出力します。

# 例

f = max(x, y) が x に等しいポリヘドロンを出力します。

```jldoctest
julia> f = TropicalPuiseuxPoly(Dict([1, 0] => 0, [0, 1] => 0), [[1, 0], [0, 1]]);

julia> polyhedron(f, [1, 0])
Polyhedron in ambient dimension 2 with Float64 type coefficients
```
