```
grumps!( 
    e       :: Estimator,
    d       :: Data{T},
    o       :: OptimizationOptions = OptimizationOptions(),
    θstart  :: StartingVector{T} = nothing,
    seo     :: StandardErrorOptions = StandardErrorOptions();
    printstructure = true
)
```

最適化を実行します。通常、θstartをnothingに設定したいだけであり、つまり自動的に選択された開始ベクトルを持つことになります。
