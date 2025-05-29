```
CountMissing(stat)
```

`missing` 値のカウントとともに `stat` を計算します。  

# 例

```
o = CountMissing(Mean())
fit!(o, [1, missing, 3])
```
