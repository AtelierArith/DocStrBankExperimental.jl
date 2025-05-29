```
 Celerite(a, b, c, d)
```

Celerite共分散関数

  * `a`: 第一項の振幅
  * `b`: 第二項の振幅
  * `c`: 共分散関数の減衰率
  * `d`: 共分散関数の`period`

$$
k(τ) = \exp(-c τ) (a \cos(d τ) + b \sin(d τ))
$$

詳細については[Foreman-Mackey et al. (2017)](https://ui.adsabs.harvard.edu/abs/2017AJ....154..220F)を参照してください。
