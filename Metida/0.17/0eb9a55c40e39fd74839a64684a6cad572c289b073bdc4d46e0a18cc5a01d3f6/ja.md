```
AutoregressiveMovingAverage()
```

自己回帰移動平均共分散タイプ。

ARMA = AutoregressiveMovingAverage()

$$
\begin{bmatrix} 1 & \gamma & \gamma\rho & \gamma\rho^2 \\
\gamma & 1 & \gamma & \gamma\rho \\
\gamma\rho & \gamma & 1 & \gamma \\
\gamma\rho^2 & \gamma\rho & \gamma & 1
\end{bmatrix}\sigma^2
$$
