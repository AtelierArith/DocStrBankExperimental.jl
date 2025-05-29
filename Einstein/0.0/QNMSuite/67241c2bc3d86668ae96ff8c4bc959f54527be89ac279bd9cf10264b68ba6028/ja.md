```
qnm_kerr_radial(ctx::QNMKerrContext{TR,TI}, A::Complex{TR}, ω::Complex{TR}) where {TR<:AbstractFloat,TI<:Integer}
```

Leaverスキームを使用して放射関数を計算します [Cook:2014cta](@cite)。

## 引数

  * `ctx`: QNMKerrContextオブジェクト。
  * `A::Complex{TR}`: 角度分離定数。
  * `ω::Complex{TR}`: QNM周波数。

## 戻り値

  * `inv_cf::Complex{TR}`: 逆連続分数。
  * `error::TR`: エラー。
  * `iter::Integer`: 繰り返し回数。

## Leaverスキーム

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

一般的な連続分数：

$$
0=\beta_0-\frac{\alpha_0 \gamma_1}{\beta_1-} \frac{\alpha_1 \gamma_2}{\beta_2-} \frac{\alpha_2 \gamma_3}{\beta_3-} \ldots
$$

連続分数の切り捨て版：

$$
\operatorname{Cf}(\mathrm{N}) \equiv \beta_0-\frac{\alpha_0 \gamma_1}{\beta_1-} \frac{\alpha_1 \gamma_2}{\beta_2-} \frac{\alpha_2 \gamma_3}{\beta_3-} \ldots \frac{\alpha_{\mathrm{N}-1} \gamma_{\mathrm{N}}}{\beta_{\mathrm{N}}+\alpha_{\mathrm{N}} \mathrm{r}_{\mathrm{N}}}
$$

この切り捨てた連続分数のn番目の逆数：

$$
\begin{aligned}
\operatorname{Cf}(\mathrm{n} ; \mathrm{N}) \equiv & \beta_n-\frac{\alpha_{n-1} \gamma_n}{\beta_{n-1}-} \frac{\alpha_{n-2} \gamma_{n-1}}{\beta_{n-2}-} \ldots \frac{\alpha_0 \gamma_1}{\beta_0} \\
& -\frac{\alpha_n \gamma_{n+1}}{\beta_{n+1}-} \frac{\alpha_{n+1} \gamma_{n+2}}{\beta_{n+2}-} \cdots \frac{\alpha_{N-1} \gamma_N}{\beta_N+\alpha_N r_N}
\end{aligned}
$$

ここで、$\operatorname{Cf}(0 ; \mathrm{N}) \equiv \operatorname{Cf}(\mathrm{N})$ かつ $0 \leq n < N$ です。

## 参考文献

  * [Cook:2014cta](@citet*)
  * [qnm/qnm/radial.py at master · duetosymmetry/qnm](https://github.com/duetosymmetry/qnm/blob/master/qnm/radial.py)

```
