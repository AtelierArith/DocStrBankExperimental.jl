```
get_drivers(model::AbstractModel)
```

モデルの `driver` オブジェクト - 大気および放射強制など - をタプル (atmos, radiation, ...) として返します。モデルにドライバーが必要ない場合は、空のタプルを返す必要があります。
