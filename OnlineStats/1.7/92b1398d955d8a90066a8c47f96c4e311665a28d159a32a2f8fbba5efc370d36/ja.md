```
Bootstrap(o::OnlineStat, nreps = 100, d = [0, 2])
```

オンライン統計ブートストラップの `nreps` 複製を `o` に対して計算します。 `fit!` への各呼び出しに対して、任意の複製は `rand(d)` 回更新されます（デフォルトはダブルまたはノッシングです）。

# 例

```
o = Bootstrap(Variance())
fit!(o, randn(1000))
confint(o, .95)
```
