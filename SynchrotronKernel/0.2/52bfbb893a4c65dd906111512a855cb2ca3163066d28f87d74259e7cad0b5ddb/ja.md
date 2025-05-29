```
synchrotron_kernel(x::Real)
```

与えられた周波数比 $x = \frac{\nu}{\nu_0}$ における最初のシンクロトロン関数と偏光成分を計算します。タプル `(K_tot, K_ort, K_par)` を返します。

```julia
K_tot = F(x)
K_ort = 0.5 * (F(x) + G(x))
K_par = 0.5 * (F(x) - G(x))
```

## シンクロトロン関数

$$
F(x) = x \int_x^\infty K_{\frac{5}{3}}(t) dt
$$

$$
G(x) = x K_{\frac{2}{3}}(x)
$$
