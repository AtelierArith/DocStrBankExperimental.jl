```
seriesoverlay(ts1, ts2)
```

両方の引数の全範囲にわたる新しい [`TSeries`](@ref) を返します。重なっている部分には最後の引数からの値が含まれます。

!!! note "非推奨の注意"
    この関数は将来的に削除されます。代わりに [`TimeSeriesEcon.overlay`](@ref) を使用してください。重要な違いは、[`TimeSeriesEcon.overlay`](@ref) では重なり部分の値が存在する最初の系列から来るのに対し、`seriesoverlay` では最後の系列から来ていたことです。


参照: [`dictoverlay`](@ref)
