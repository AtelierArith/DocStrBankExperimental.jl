```
HeterogeneousToeplitz()
```

Heterogeneous toeplitz covariance type. Only for G matrix.

TOEPH = HeterogeneousToeplitz()

$$
\begin{bmatrix}
\sigma_a^2 & \rho_1 \sigma_a \sigma_b & \rho_2 \sigma_a \sigma_c & \rho_3 \sigma_a \sigma_d \\
\rho_1 \sigma_b \sigma_a & \sigma_b^2 & \rho_1 \sigma_b \sigma_c & \rho_2 \sigma_b \sigma_d \\
\rho_2 \sigma_c \sigma_a & \rho_1 \sigma_c \sigma_b & \sigma_c^2 & \rho_1 \sigma_c \sigma_d \\
\rho_3 \sigma_d \sigma_a & \rho_2 \sigma_d \sigma_b & \rho_1 \sigma_d \sigma_c & \sigma_d^2
\end{bmatrix}
$$
