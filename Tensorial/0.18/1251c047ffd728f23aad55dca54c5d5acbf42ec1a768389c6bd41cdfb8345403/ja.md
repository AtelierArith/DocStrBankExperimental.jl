```
rotmatz(θ::Number)
```

`z` 軸周りの回転行列を構築します。

$$
\bm{R}_z = \begin{bmatrix}
\cos{\theta} & -\sin{\theta} & 0 \\
\sin{\theta} &  \cos{\theta} & 0 \\
0 & 0 & 1
\end{bmatrix}
$$
