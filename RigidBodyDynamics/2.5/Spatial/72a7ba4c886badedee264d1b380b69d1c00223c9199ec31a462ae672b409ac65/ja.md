```julia
struct SpatialInertia{T}
```

空間慣性、または慣性行列は、剛体の質量分布を表します。

フレーム $i$ で表現された空間慣性は次のように定義されます：

$$
I^i =
\int_{B}\rho\left(x\right)\left[\begin{array}{cc}
\hat{p}^{T}\left(x\right)\hat{p}\left(x\right) & \hat{p}\left(x\right)\\
\hat{p}^{T}\left(x\right) & I
\end{array}\right]dx=\left[\begin{array}{cc}
J & \hat{c}\\
\hat{c}^{T} & mI
\end{array}\right]
$$

ここで、$\rho(x)$ は点 $x$ の密度であり、$p(x)$ はフレーム $i$ で表現された点 $x$ の座標です。$J$ は質量モーメント、$m$ は総質量、$c$ は「交差部分」、すなわち質量 $m$ でスケーリングされた重心位置です。

!!! warning
    `SpatialInertia` の `moment` フィールドは、その `frame` の原点に関する慣性モーメントであり、重心に関するものではありません。

