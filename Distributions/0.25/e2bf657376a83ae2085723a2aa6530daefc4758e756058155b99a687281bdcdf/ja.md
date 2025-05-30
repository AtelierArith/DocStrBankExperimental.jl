```
Uniform(a,b)
```

*区間 $[a, b]$ における* *連続一様分布* の確率密度関数は

$$
f(x; a, b) = \frac{1}{b - a}, \quad a \le x \le b
$$

```julia
Uniform()        # [0, 1] 上の一様分布
Uniform(a, b)    # [a, b] 上の一様分布

params(d)        # パラメータを取得、すなわち (a, b)
minimum(d)       # 下限を取得、すなわち a
maximum(d)       # 上限を取得、すなわち b
location(d)      # 位置パラメータを取得、すなわち a
scale(d)         # スケールパラメータを取得、すなわち b - a
```

外部リンク

  * [Uniform distribution (continuous) on Wikipedia](http://en.wikipedia.org/wiki/Uniform_distribution_(continuous))
