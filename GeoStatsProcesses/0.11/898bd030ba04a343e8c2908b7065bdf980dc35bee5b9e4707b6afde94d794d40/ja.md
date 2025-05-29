```
IndicatorProcess(func, prob)
```

多変量地質統計的 `func`ション（例：多変量共分散）と事前の `prob`能力を持つ指標プロセス。

```
IndicatorProcess(transiogram, prob=proportions(transiogram))
```

または、`transiogram`から指標プロセスを構築します。

## 例

```julia
# 共分散と明示的な確率
IndicatorProcess([1.0 0.5; 0.5 1.0] * SphericalCovariance(), [0.8, 0.2])

# トランジオグラムと暗黙的な確率
IndicatorProcess(LinearTransiogram())

# トランジオグラムと明示的な確率
IndicatorProcess(ExponentialTransiogram(), [0.8, 0.2])
```
