```
tree3morton(t::AbstractVector) -> m::Integer
```

オクツリー座標を与えると、対応するモートン番号を返します。

# 例

```jldoctest
julia> tree3morton([2,1,3])
67
```
