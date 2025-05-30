```
batchview(d::AbstractDiskDataProvider, size=d.batchsize; kwargs...)
```

DiskDataProviderの作成時に定義されたバッチサイズでバッチを反復するバッチイテレータを作成します。
