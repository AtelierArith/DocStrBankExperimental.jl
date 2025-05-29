```
GroupBy(T, stat)
```

各グループ（型 `T`）のために `stat` を更新します。単一の観測値は、2つの要素を持つ（名前付き）タプルまたはペアです。

# 例

```
x = rand(Bool, 10^5)
y = x .+ randn(10^5)
fit!(GroupBy(Bool, Series(Mean(), Extrema())), zip(x,y))
```
