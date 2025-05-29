```
flux_ec(u_ll, u_rr, orientation, equations::InviscidBurgersEquation1D)
```

エントロピー保存、対称フラックスの無粘性バーガーズ方程式。

$$
F(u_L, u_R) = \frac{u_L^2 + u_L u_R + u_R^2}{6}
$$
