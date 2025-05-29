```
yarkp2adot(A2, a, e, μ_S)
```

Yarkovsky 効果による平均半長軸ドリフトを返します

$$
\begin{align*}
    \left\langle\dot{a}\right\rangle & = \frac{2A_2(1-e^2)}{n}\left(\frac{1 \ \text{AU}}{p}\right)^2 \\
    & = \frac{2A_2}{(1-e^2)\sqrt{a\mu_\odot}}(1 \ \text{AU})^2,
\end{align*}
$$

ここで、$A_2$ は Yarkovsky パラメータ、$\mu_\odot = GM_\odot$ は太陽の重力パラメータ、$e$ は離心率、$n = \sqrt{\mu/a^3}$ は平均運動、$p = a(1-e^2)$ は半主軸、$a$ は半長軸です。

# 引数

  * `A2`: Yarkovsky パラメータ。
  * `a`: 半長軸。
  * `e`: 離心率。
  * `μ_S`: 太陽の質量パラメータ。

!!! reference
    See https://doi.org/10.1016/j.icarus.2013.02.004.

