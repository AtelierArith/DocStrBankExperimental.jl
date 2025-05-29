```
fitted_mean(gas::ScoreDrivenModel{D, T}, observations::Vector{T};
            initial_params::Matrix{T}=stationary_initial_params(gas)) where {D, T}
```

サンプル内系列のフィッティングされた平均、すなわち、`gas`のフィッティングされたパラメータを使用して各時間ステップでの予測分布の平均を返します。
