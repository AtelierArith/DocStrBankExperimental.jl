```
genmean(a, p)
```

実数値配列の指数 `p` に対する一般化/冪平均を返します。すなわち、$\left( \frac{1}{n} \sum_{i=1}^n a_i^p \right)^{\frac{1}{p}}$ であり、ここで `n = length(a)` です。`p == 0` の場合は幾何平均と見なされます。
