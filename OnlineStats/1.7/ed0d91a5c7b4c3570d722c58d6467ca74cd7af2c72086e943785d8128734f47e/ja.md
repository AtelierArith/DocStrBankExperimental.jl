```
ReservoirSample(k::Int, T::Type = Float64)
```

サイズ `k` の置換なしサンプルを作成します。 `n` 回の観察を通過した後、観察がサンプルに含まれる確率は `1 / n` です。

# 例

```
fit!(ReservoirSample(100, Int), 1:1000)
```
