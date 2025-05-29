```
kde = KDEDist(data)
```

Distributions.jl インターフェースに従う一変量分布。提供された入力データとオプションのバンド幅スケールファクターを使用して、KernelDensity.jl を使用して 1D カーネル密度推定器を作成します。

Octofitter モデルの事前分布として使用するのに適しています。
