```
cubic_b_spline_kernel(δ, L)
```

家族内のボンドに重みを付けるために使用される三次Bスプラインカーネル関数$\omega$。カーネル関数は次のように定義されます。

$$
\begin{aligned}
\xi &= \frac{L}{\delta} \; , \\
\omega &= \left\{
    \begin{array}{ll}
        \frac{2}{3} - 4 \xi^2 + 4 \xi^3 & \quad \text{if} \; 0 < \xi \leq 0.5 \; , \\[3pt]
        \frac{4}{3} - 4 \xi + 4 \xi^2 - \frac{4}{3} \xi^3 & \quad \text{if} \; 0.5 < \xi \leq 1 \; , \\[3pt]
        0 & \quad \text{else} \; ,
    \end{array}
    \right.
\end{aligned}
$$

ホライズン$\delta$と初期ボンド長$L$を持つ。
