cartesian2tree(c::AbstractVector) -> t::AbstractVector

2次元のデカルト座標を与えると、対応するクワッドツリー座標を返します。

# 例

```jldoctest
julia> cartesian2tree([5,2])
3-element Array{Int64,1}:
 2
 1
 3
```
