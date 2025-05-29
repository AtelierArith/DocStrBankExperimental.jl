```
scale(f=std, x, y=f(skipmissing(x)))
```

配列 `x` をスカラー `y` でその場でスケーリングします。

!!! warning
    これは値をスケーリングするだけで、Rの `scale` とは異なり、値をセンタリングしません。その機能については `StatsBase.zscore` を参照してください。


参照: [`scale`](@ref)
