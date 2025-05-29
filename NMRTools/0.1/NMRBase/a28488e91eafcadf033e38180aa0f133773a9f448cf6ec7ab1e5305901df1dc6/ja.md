```
SineWindow(offset, endpoint, power, tmax)
```

サイン/コサイン関数による乗算を表す抽象ウィンドウ関数。取得時間は `tmax` です。

$$
\left[\sin\left(
    \pi\cdot\mathrm{offset} +
    \frac{\left(\mathrm{end} - \mathrm{offset}\right)\pi t}{\mathrm{tmax}}
    \right)\right]^\mathrm{power}
$$

`CosWindow`、`Cos²Window`、または `GeneralSineWindow` に特化します。

# 引数

  * `offset`: 初期値は $\sin(\mathrm{offset}\cdot\pi)$ (0 から 1)
  * `endpoint`: 初期値は $\sin(\mathrm{endpoint}\cdot\pi)$ (0 から 1)
  * `pow`: サインの指数
