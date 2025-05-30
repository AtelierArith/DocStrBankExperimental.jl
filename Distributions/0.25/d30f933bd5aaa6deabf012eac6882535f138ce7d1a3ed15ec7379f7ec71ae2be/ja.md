```
ポアソン分布(λ)
```

*ポアソン分布*は、発生の平均率`λ`が与えられたときに、単位時間間隔内に発生する独立したイベントの数を記述します。

$$
P(X = k) = \frac{\lambda^k}{k!} e^{-\lambda}, \quad \text{ for } k = 0,1,2,\ldots.
$$

```julia
Poisson()        # レートパラメータ1のポアソン分布
Poisson(lambda)       # レートパラメータlambdaのポアソン分布

params(d)        # パラメータを取得します。すなわち(λ,)
mean(d)          # 平均到着率を取得します。すなわちλ
```

外部リンク:

  * [ポアソン分布 - Wikipedia](http://en.wikipedia.org/wiki/Poisson_distribution)
