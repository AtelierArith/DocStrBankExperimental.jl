```
AutoregressiveMovingAverage()
```

Autoregressive moving average covariance type.

ARMA = AutoregressiveMovingAverage()

$$
\begin{bmatrix} 1 & \gamma & \gamma\rho & \gamma\rho^2 \\
\gamma & 1 & \gamma & \gamma\rho \\
\gamma\rho & \gamma & 1 & \gamma \\
\gamma\rho^2 & \gamma\rho & \gamma & 1
\end{bmatrix}\sigma^2
$$
