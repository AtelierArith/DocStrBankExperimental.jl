```
SkipMissing(stat)
```

`missing` 値をスキップする OnlineStat のラッパーです。

# 例

```
o = SkipMissing(Mean())

fit!(o, [1, missing, 3])
```
