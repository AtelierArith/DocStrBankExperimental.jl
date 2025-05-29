```
Group(stats::OnlineStat...)
Group(; stats...)
Group(collection)
```

いくつかのスカラー入力統計からベクトル入力統計を作成します。新しい観測値 `y` に対して、`y[i]` は `stats[i]` に送られます。

# 例

```
x = randn(100, 2)

fit!(Group(Mean(), Mean()), eachrow(x))
fit!(Group(Mean(), Variance()), eachrow(x))

o = fit!(Group(m1 = Mean(), m2 = Mean()), eachrow(x))
o.stats.m1
o.stats.m2

o = Group(fill(Mean(), 10))
fit!(o, eachrow(randn(100, 10)))
```
