```julia
struct IsAnalytic <: EHTModels.DensityAnalytic
```

モデルが解析的であることを示すトレイトを定義します。これは通常、抽象モデルと共に使用され、モデルが解析的なフーリエ変換および/または画像を持つかどうかを指定するために使用されます。
