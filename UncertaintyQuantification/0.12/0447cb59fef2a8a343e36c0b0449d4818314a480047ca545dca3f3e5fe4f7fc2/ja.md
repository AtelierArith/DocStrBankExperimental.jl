```
SubSetSimulation(n::Integer, target::Float64, levels::Integer, proposal::UnivariateDistribution)
```

サブセットシミュレーションのプロパティを定義します。ここで、`n` は初期サンプルの数、`target` は各レベルでの失敗の目標確率、`levels` は最大レベル数、`proposal` はマルコフ連鎖モンテカルロのための提案分布です。

# 例

```jldoctest
julia> SubSetSimulation(100, 0.1, 10, Uniform(-0.2, 0.2))
SubSetSimulation(100, 0.1, 10, Uniform{Float64}(a=-0.2, b=0.2))
```

# 参考文献

[auEstimationSmallFailure2001](@cite)
