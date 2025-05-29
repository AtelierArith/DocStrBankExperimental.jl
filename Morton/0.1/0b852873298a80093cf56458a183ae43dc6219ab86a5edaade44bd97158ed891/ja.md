```
morton3tree(m::Integer) -> t::AbstractVector
```

モートン番号を与えると、対応するオクトリー座標を返します。

# 例

```jldoctest
julia> morton3tree(67)
3-element Array{Any,1}:
 2
 1
 3
```
