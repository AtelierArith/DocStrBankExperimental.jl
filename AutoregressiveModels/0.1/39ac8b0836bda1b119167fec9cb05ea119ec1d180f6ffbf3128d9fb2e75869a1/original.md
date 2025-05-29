```
VARProcess(B::AbstractMatrix, B0=nothing; copy::Bool=false)
```

Return a vector autoregressive process $Y_t$ defined as

$$
Y_t = B_0 + \sum_{l=1}^p B_l Y_{t-l} + \ε_t
$$

where the autoregressive coefficients $\{\B_l\}_l$ are collected in matrix `B` by column and the optional intercept $B_0$ is in a vector `B0`.
