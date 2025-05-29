1Dセグメント/2Dポリゴン/3D多面体の内部に点があるかどうかを判定します。内部にあれば1を、外部にあれば0を、任意の面上にあれば-1を返します。

```
pinpoly(point::NTuple{dim,Float64}, faces::NTuple{N,NTuple{dim,NTuple{dim,Float64}}}, start::NTuple{dim,Float64}, stop::NTuple{dim,Float64}) where N where dim
```

`faces`: 境界上のすべての`face`のノード位置のタプル。`face`は1/2/3D空間におけるノード/セグメント/三角形を指します。ノードの配置順序は、時計回りまたは反時計回りのどちらでも構いません。

`point`: 点の位置。

`start`: すべてのノードの中での最小座標

`stop`: すべてのノードの中での最大座標

例:

```
P = (
    (0., 0., 0.),
    (1., 0., 0.),
    (0., 1., 0.),
    (0., 0., 1.)
    )
faces = (
    (P[1], P[2], P[3]), 
    (P[1], P[2], P[4]), 
    (P[2], P[3], P[4]), 
    (P[1], P[3], P[4])
    )
start = (0., 0., 0.)
stop = (1., 1., 1.)

points = (
    ( 0.1,  0.1,  0.01), 
    ( 0.1,  0.1,    0.), 
    ( 0.1,  0.1,  -0.1), 
    (  0.,   0.,   0.5), 
    (  0.,  0.1,   0.1), 
    (  0.,   0.,   1.1),
    ( 1/4,  1/4,   1/2),
    )

for point in points
    println(point," => ", pinpoly(point, faces, start, stop))
end
```

参考文献

[1] https://wrf.ecse.rpi.edu//Research/Short_Notes/pnpoly.html.

[2] https://blog.csdn.net/u012138730/article/details/80235813
