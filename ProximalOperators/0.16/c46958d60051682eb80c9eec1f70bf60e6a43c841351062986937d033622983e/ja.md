```
PointwiseMinimum(f_1, ..., f_k)
```

与えられた関数 `f_1` から `f_k` までの点ごとの最小値を返します。つまり、関数

$$
g(x) = \min\{f_1(x), ..., f_k(x)\}
$$

に相当します。

注意してください。`g` は一般に非凸関数です。
