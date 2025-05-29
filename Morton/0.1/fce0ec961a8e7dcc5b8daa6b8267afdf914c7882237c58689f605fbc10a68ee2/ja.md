cartesian3tree(c::AbstractVector) -> t::AbstractVector

3次元デカルト座標を与えると、対応するオクツリー座標を返します。

# 例

```jldoctest
julia> cartesian3tree([5,2,1])
3-element Array{Int64,1}:
 2
 1
 3
```
