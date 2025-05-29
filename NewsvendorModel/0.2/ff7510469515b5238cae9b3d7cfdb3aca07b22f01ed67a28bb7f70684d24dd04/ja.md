```
leftover(anp::AbstractNewsvendorProblem, q)
```

在庫量 q のときの期待残余在庫を計算します。

$$
E[\textrm{leftover}] = \int_{-\infty}0^q(q - x)f(x)dx 
$$
