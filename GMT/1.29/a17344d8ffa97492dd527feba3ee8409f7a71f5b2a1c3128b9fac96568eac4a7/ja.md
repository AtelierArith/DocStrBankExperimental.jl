```
gdaldrivers(type="raster"; out::Bool=false)
```

このGMT.jlインストールで利用可能なすべてのGDALドライバをリストします。デフォルトではラスタードライバの名前を印刷しますが、`type="vector"`の場合はベクタードライバの名前を印刷します。`out=true`の場合、テーブルを印刷する代わりに、テーブルの4つの列を別々の4つのベクタとして返します。
