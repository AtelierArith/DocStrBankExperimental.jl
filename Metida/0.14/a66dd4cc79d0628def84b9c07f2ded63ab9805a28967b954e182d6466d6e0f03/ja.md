```
HeterogeneousAutoregressive()
```

異種自己回帰共分散タイプ。

ARH = HeterogeneousAutoregressive()

$$
\begin{bmatrix}
\sigma_a^2 & \rho\sigma_a\sigma_b & \rho^2\sigma_a\sigma_c & \rho^3\sigma_a\sigma_d \\
\rho\sigma_b\sigma_a & \sigma_b^2 & \rho\sigma_b\sigma_c & \rho^2\sigma_b\sigma_d \\
\rho^2\sigma_c\sigma_a & \rho\sigma_c\sigma_b & \sigma_c^2 & \rho\sigma_c\sigma_d \\
\rho^3\sigma_d\sigma_a & \rho^2\sigma_d\sigma_b & \rho\sigma_d\sigma_c & \sigma_d^2
\end{bmatrix}
$$
