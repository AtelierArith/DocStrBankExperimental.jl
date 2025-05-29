```
rotmaty(θ::Number)
```

`y` 軸周りの回転行列を構築します。

$$
\bm{R}_y = \begin{bmatrix}
\cos{\theta} & 0 & \sin{\theta} \\
0 & 1 & 0 \\
-\sin{\theta} & 0 & \cos{\theta}
\end{bmatrix}
$$
