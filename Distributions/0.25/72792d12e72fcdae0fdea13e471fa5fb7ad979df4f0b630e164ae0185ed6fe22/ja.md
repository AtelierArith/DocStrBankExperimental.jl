```
Hypergeometric(s, f, n)
```

*ハイパージオメトリック分布*は、成功が`s`、失敗が`f`の有限母集団から、置換なしで`n`回の抽出を行ったときの成功の数を表します。

$$
P(X = k) = {{{s \choose k} {f \choose {n-k}}}\over {s+f \choose n}}, \quad \text{for } k = \max(0, n - f), \ldots, \min(n, s).
$$

```julia
Hypergeometric(s, f, n)  # 成功がs、失敗がfの母集団に対するハイパージオメトリック分布と
                         # n回の試行のシーケンス。

params(d)       # パラメータを取得します。すなわち (s, f, n)
```

外部リンク

  * [ハイパージオメトリック分布 - Wikipedia](http://en.wikipedia.org/wiki/Hypergeometric_distribution)
