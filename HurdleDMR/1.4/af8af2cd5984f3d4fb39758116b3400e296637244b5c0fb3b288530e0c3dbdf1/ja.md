```
PositivePoisson(λ)
```

*PositivePoisson分布*（別名ゼロ切断ポアソン、ZTP）は、発生率`λ`が与えられ、重要なことに数がゼロでないことが与えられた場合に、単位時間間隔内に発生する独立したイベントの数を記述します。

$$
P(X = k) = \frac{λ^k}{k!(1-e^{-λ})} e^{-λ}, \quad \text{ for } k = 1,2,\ldots.
$$

```julia
PositivePoisson()        # レートパラメータ1のPositivePoisson分布
PositivePoisson(lambda)       # レートパラメータlambdaのPositivePoisson分布

params(d)        # パラメータを取得します。すなわち(λ,)
mean(d)          # 平均到着率を取得します。すなわちλ
```

外部リンク：

  * [PositivePoisson分布のWikipedia](https://en.wikipedia.org/wiki/Zero-truncated_Poisson_distribution)
