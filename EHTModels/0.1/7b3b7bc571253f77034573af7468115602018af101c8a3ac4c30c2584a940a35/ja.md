```julia
struct NotAnalytic <: EHTModels.DensityAnalytic
```

モデルが解析的であることを示すトレイトを定義します。これは通常、抽象モデルと共に使用され、モデルが簡単な解析的フーリエ変換および/または強度関数を持っているかどうかを指定するために使用されます。
