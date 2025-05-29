```
refit!(m::QuantileRegression,
      [y::FPVector ;
       verbose::Bool=false,
       quantile::Union{Nothing,
       AbstractFloat}=nothing,
      ]
)
```

`QuantileRegression`モデルを応答、重み、および分位点の新しい値で再適合させます。この関数は、`m`が正しく初期化されていることを前提としています。
