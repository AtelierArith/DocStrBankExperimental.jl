```
create_basis_DPDKs(args...; kwargs...)
```

Create the candidate basis kernels according the following formula:

$$
K_m(u, v) = 1 - |q_m^\top (u - v) / (c_m \cdot κ)|
$$

# References

1. Han, B., Shang, C., & Huang, D. (2020). Multiple kernel learning-aided robust optimization: learning algorithm, computational tractability, and usage in multi-stage decision-making. European Journal of Operational Research. https://doi.org/10.1016/j.ejor.2020.11.027.
