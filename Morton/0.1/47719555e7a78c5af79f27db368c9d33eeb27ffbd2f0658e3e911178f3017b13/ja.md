```
tree2morton(t::AbstractVector) -> m::Integer
```

クワッドツリー座標を与えると、対応するモートン番号を返します。

# 例

```jldoctest
julia> tree2morton([2,1,3])
19
```
