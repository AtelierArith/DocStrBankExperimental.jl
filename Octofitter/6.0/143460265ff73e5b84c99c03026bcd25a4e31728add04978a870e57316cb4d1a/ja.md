```
initialize!(model::LogDensityModel, fixed_params=nothing; kwargs...)
```

オプションの固定パラメータを名前付きタプルとして提供してモデルを初期化します。固定パラメータは最適化およびサンプリング中に一定に保たれます。
