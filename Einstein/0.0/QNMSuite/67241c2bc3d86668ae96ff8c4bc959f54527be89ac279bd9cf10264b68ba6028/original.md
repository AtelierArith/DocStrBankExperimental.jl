```
qnm_kerr_radial(ctx::QNMKerrContext{TR,TI}, A::Complex{TR}, ω::Complex{TR}) where {TR<:AbstractFloat,TI<:Integer}
```

Calculate the radial function using the Leaver scheme [Cook:2014cta](@cite).

## Arguments

  * `ctx`: QNMKerrContext object.
  * `A::Complex{TR}`: Angular separation constant.
  * `ω::Complex{TR}`: QNM frequency.

## Returns

  * `inv_cf::Complex{TR}`: The inverse continued fraction.
  * `error::TR`: The error.
  * `iter::Integer`: The number of iterations.

## Leaver scheme

$$
\begin{aligned}
& D_0=\delta=1+s+2 \xi \\
& D_1=4 p-2 \alpha+\gamma-\delta-2 \\
& D_2=2 \alpha-\gamma+2 \\
& D_3=\alpha(4 p-\delta)-\sigma, \\
& D_4=\alpha(\alpha-\gamma+1)
\end{aligned}
$$

$$
\begin{aligned}
\alpha_n & \equiv n^2+\left(D_0+1\right) n+D_0 \\
\beta_n & \equiv-2 n^2+\left(D_1+2\right) n+D_3 \\
\gamma_n & \equiv n^2+\left(D_2-3\right) n+D_4-D_2+2
\end{aligned}
$$

The general continued fraction:

$$
0=\beta_0-\frac{\alpha_0 \gamma_1}{\beta_1-} \frac{\alpha_1 \gamma_2}{\beta_2-} \frac{\alpha_2 \gamma_3}{\beta_3-} \ldots
$$

The truncated version of the continued fraction:

$$
\operatorname{Cf}(\mathrm{N}) \equiv \beta_0-\frac{\alpha_0 \gamma_1}{\beta_1-} \frac{\alpha_1 \gamma_2}{\beta_2-} \frac{\alpha_2 \gamma_3}{\beta_3-} \ldots \frac{\alpha_{\mathrm{N}-1} \gamma_{\mathrm{N}}}{\beta_{\mathrm{N}}+\alpha_{\mathrm{N}} \mathrm{r}_{\mathrm{N}}}
$$

The nth inversion of this truncated continued fraction:

$$
\begin{aligned}
\operatorname{Cf}(\mathrm{n} ; \mathrm{N}) \equiv & \beta_n-\frac{\alpha_{n-1} \gamma_n}{\beta_{n-1}-} \frac{\alpha_{n-2} \gamma_{n-1}}{\beta_{n-2}-} \ldots \frac{\alpha_0 \gamma_1}{\beta_0} \\
& -\frac{\alpha_n \gamma_{n+1}}{\beta_{n+1}-} \frac{\alpha_{n+1} \gamma_{n+2}}{\beta_{n+2}-} \cdots \frac{\alpha_{N-1} \gamma_N}{\beta_N+\alpha_N r_N}
\end{aligned}
$$

with $\operatorname{Cf}(0 ; \mathrm{N}) \equiv \operatorname{Cf}(\mathrm{N})$ and $0 \leq n < N$

## References

  * [Cook:2014cta](@citet*)
  * [qnm/qnm/radial.py at master · duetosymmetry/qnm](https://github.com/duetosymmetry/qnm/blob/master/qnm/radial.py)
