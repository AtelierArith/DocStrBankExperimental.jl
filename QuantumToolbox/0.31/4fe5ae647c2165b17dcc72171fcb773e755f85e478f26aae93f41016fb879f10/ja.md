```
n_thermal(ω::Real, ω_th::Real)
```

調和振動子モードの周波数 $\omega$ に対する熱平衡における光子の数を返します。温度は $\omega_{\textrm{th}} \equiv k_B T / \hbar$ で表されます：

$$
n(\omega, \omega_{\textrm{th}}) = \frac{1}{e^{\omega/\omega_{\textrm{th}}} - 1},
$$

ここで、$\hbar$ は縮退プランク定数、$k_B$ はボルツマン定数です。
