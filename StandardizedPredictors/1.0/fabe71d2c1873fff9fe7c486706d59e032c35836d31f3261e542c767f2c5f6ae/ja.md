```
scale(f=std, x, y=f(skipmissing(x)))
```

配列 `x` をスカラー `y` でスケーリングします。

!!! warning
    これは値をスケーリングするだけで、Rの `scale` とは異なり、値をセンタリングしません。その機能については `StatsBase.zscore` を参照してください。


関連情報として [`scale!`](@ref) を参照してください。
