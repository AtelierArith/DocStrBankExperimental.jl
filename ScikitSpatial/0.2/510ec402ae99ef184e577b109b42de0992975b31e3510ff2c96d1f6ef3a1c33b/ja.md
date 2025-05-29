```
angle_between(u::AbstractVector, v::AbstractVector) -> Float
```

2つのベクトルの間の角度を計算します。角度はラジアンで返されます。

# 例

```jldoctest
julia> angle_between([1, 0], [1, 0])
0.0

julia> round(angle_between([1,1], [1,0]), digits=3)
0.785

julia> round(angle_between([1, 0], [0, 1]), digits=3)
1.571

julia> round(angle_between([-1, 0], [1, 0]), digits=3)
3.142

julia> round(angle_between([1,0,0], [1,1,1]), digits=3)
0.955
```
