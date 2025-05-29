tree3cartesian(t::AbstractVector) -> c::AbstractVector

オクトリー座標を与えると、対応する3-Dデカルト座標を返します。

# 例

```jldoctest
julia> tree3cartesian([2,1,3])
3-element Array{Int64,1}:
 5
 2
 1
```
