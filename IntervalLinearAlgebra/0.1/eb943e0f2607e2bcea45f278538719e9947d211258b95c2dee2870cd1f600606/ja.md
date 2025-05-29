```
@affinevars(x...)
```

[`AffineExpression`](@ref)を表すために使用される変数を構築するマクロです。

### 例

```jldoctest
julia> @affinevars x
1-element Vector{AffineExpression{Int64}}:
 x

julia> @affinevars x y z
3-element Vector{AffineExpression{Int64}}:
 x
 y
 z

julia> @affinevars x[1:4]
4-element Vector{AffineExpression{Int64}}:
 x1
 x2
 x3
 x4
```
