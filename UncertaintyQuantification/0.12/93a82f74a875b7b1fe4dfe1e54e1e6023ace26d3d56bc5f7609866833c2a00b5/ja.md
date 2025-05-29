```
SubSetInfinity(n::Integer, target::Float64, levels::Integer, s::Real)
```

`n`は初期サンプルの数、`target`は各レベルでの失敗の目標確率、`levels`は最大レベル数、`s`は提案サンプルの標準偏差を表すSubset-∞シミュレーションの特性を定義します。

# 例

```jldoctest
julia> SubSetInfinity(100, 0.1, 10, 0.5)
SubSetInfinity(100, 0.1, 10, 0.5)
```

# 参考文献

[auRareEventSimulation2016](@cite)

[patelliEfficientMonteCarlo2015](@cite)
