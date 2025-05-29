```
synchrotron_intensity(x::Real)
```

偏光成分なしで全体のシンクロトロンカーネルを計算します。 [`F`](@ref) のラッパーです。

$$
F(x) = x \int_x^\infty K_{\frac{5}{3}}(t) dt
$$
