```
rotmatx(θ::Number)
```

`x` 軸周りの回転行列を構築します。

$$
\bm{R}_x = \begin{bmatrix}
1 & 0 & 0 \\
0 & \cos{\theta} & -\sin{\theta} \\
0 & \sin{\theta} &  \cos{\theta}
\end{bmatrix}
$$
