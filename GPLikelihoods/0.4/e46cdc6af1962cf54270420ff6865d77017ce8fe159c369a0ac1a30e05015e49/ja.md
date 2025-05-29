```
NBParamSuccess(successes)
```

成功の数を `successes` とし、成功の確率を `invlink(f)` とする負の二項分布のパラメータ化です。これは [Distributions.jl](https://juliastats.org/Distributions.jl/latest/univariate/#Distributions.NegativeBinomial) で使用されている定義に対応しています。

$$
  p(y|\text{successes}, p=\text{invlink}(f)) = \frac{\Gamma(y+\text{successes})}{y! \Gamma(\text{successes})} p^\text{successes} (1 - p)^y
$$
