```
Skellam(μ1, μ2)
```

*スケラム分布*は、レート`μ1`および`μ2`を持つ二つの独立した[`ポアソン`](@ref)変数の差を表します。

$$
P(X = k) = e^{-(\mu_1 + \mu_2)} \left( \frac{\mu_1}{\mu_2} \right)^{k/2} I_k(2 \sqrt{\mu_1 \mu_2}) \quad \text{for integer } k
$$

ここで、$I_k$は第一種の修正ベッセル関数です。

```julia
Skellam(μ1, μ2)     # スケラム分布は、期待値がそれぞれμ1およびμ2の二つのポアソン変数の差に対するものです。

params(d)           # パラメータを取得します。すなわち(μ1, μ2)
```

外部リンク:

  * [スケラム分布 - Wikipedia](http://en.wikipedia.org/wiki/Skellam_distribution)
