```
distance(x, y)
distance(region::Parallelepiped{D,T},x,y)
```

2点間の距離。

点 `x` と `y` のみが提供される場合、ユークリッド距離が計算されます。

`region` が提供される場合、自動的に周期境界条件が有効であると仮定され、2点間の最小の距離が返されます。

```jldoctest; setup=:(using BloqadeLattices)
julia> distance((0.0, 0.0), (1.0, 1.0))
1.4142135623730951

julia> bounds = zeros(2,2); bounds[:,1] .= (3, 0); bounds[:,2] .= (0, 3);

julia> distance(Parallelepiped(bounds), (0.5, 0.5), (2.5, 2.5))
1.4142135623730951
```
