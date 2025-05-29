```
AffineExpression{T}
```

アフィン式を表すデータ構造、例えば $x+2y+z+4$ のようなものです。

### 例

```jldoctest
julia> @affinevars x y z
3-element Vector{AffineExpression{Int64}}:
 x
 y
 z

julia> p1 = x + 2y + z + 4
x+2y+z+4
```
