tree2cartesian(t::AbstractVector) -> c::AbstractVector

クワッドツリー座標を与えると、対応する2次元デカルト座標を返します。

# 例

```jldoctest
julia> tree2cartesian([2,1,3])
2-element Array{Int64,1}:
 5
 2
```
