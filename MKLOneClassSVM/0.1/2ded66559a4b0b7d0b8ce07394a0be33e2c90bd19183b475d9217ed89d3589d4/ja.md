```
create_basis_DPDKs(args...; kwargs...)
```

候補基底カーネルを次の式に従って作成します：

$$
K_m(u, v) = 1 - |q_m^\top (u - v) / (c_m \cdot κ)|
$$

# 参考文献

1. Han, B., Shang, C., & Huang, D. (2020). Multiple kernel learning-aided robust optimization: learning algorithm, computational tractability, and usage in multi-stage decision-making. European Journal of Operational Research. https://doi.org/10.1016/j.ejor.2020.11.027.
