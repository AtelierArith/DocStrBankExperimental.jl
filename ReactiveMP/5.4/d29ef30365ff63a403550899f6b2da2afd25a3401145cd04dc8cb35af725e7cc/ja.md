```
FullSampling <: CVISamplingStrategy
FullSampling(samples::Int = 10)
```

複数のサンプルを分布から引き出すサンプリング戦略です。

# 引数

  * `samples::Int`: 各分布から引き出すサンプルの数。デフォルトは10です。

# 例

```julia
# より正確な近似のために100サンプルを使用
strategy = FullSampling(100)
```
