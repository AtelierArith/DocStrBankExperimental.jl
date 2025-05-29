```
morton2tree(m::Integer) -> t::AbstractVector
```

モートン番号を与えると、対応するクワッドツリー座標を返します。

# 例

```jldoctest
julia> morton2tree(19)
3-element Array{Any,1}:
 2
 1
 3
```
