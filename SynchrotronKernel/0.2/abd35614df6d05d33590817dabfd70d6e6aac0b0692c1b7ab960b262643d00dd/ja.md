```
synchrotron_polarisation(x::Real)
```

与えられた周波数比 $x = \frac{\nu}{\nu_0}$ における第二のシンクロトロン関数を計算します。 `(K_ort, K_par)` のタプルを返します。

```julia
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
