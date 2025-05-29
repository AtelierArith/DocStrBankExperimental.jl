```
project(M::AbstractSphere, p)
```

点 `p` を埋め込みから [`Sphere`](@ref) `M` へ投影します。

$$
\operatorname{proj}(p) = \frac{p}{\lVert p \rVert},
$$

ここで、$\lVert⋅\rVert$ は $m=1$ の場合のベクトルに対する通常の2ノルム、$m>1$ の場合のフロベニウスノルムを示します。
