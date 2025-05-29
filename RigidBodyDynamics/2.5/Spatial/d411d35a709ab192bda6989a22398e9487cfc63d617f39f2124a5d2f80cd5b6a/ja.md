```julia
struct Momentum{T}
```

`Momentum`は`SpatialInertia`と`Twist`の積であり、すなわち

$$
h^i =
\left(\begin{array}{c}
k^{i}\\
l^{i}
\end{array}\right) =
I^i T^{i, j}_k
$$

ここで、$I^i$はフレーム$i$で表現された特定の物体の空間慣性であり、$T^{i, j}_k$はフレーム$i$で表現された慣性フレーム$j$に対するフレーム$k$（物体に取り付けられた）のツイストです。$k^i$は角運動量であり、$l^i$は線運動量です。
