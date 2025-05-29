```
NBParamFailure(failures)
```

失敗の数を `failures` とし、成功の確率を `invlink(f)` とする負の二項分布のパラメータ化です。これは、[Wikipedia](https://en.wikipedia.org/wiki/Negative_binomial_distribution) で使用されている定義に対応しています。

$$
  p(y|\text{failures}, p=\text{invlink}(f)) = \frac{\Gamma(y+\text{failures})}{y! \Gamma(\text{failures})} p^y (1 - p)^{\text{failures}}
$$
