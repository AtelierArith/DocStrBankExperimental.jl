```
Series(stats)
Series(stats...)
Series(; stats...)
```

1つのデータストリームのためのコレクション stats を追跡します。

# 例

```
s = Series(Mean(), Variance())
fit!(s, randn(1000))
```
