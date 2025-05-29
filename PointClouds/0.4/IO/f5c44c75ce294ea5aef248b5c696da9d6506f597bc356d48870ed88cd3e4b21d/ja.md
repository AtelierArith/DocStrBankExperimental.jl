```
scanner_channel([T], p::PointRecord)
scanner_channel([T], points, inds = :)
```

マルチチャネルシステムのチャネル/スキャナーヘッドを取得します。これは0から3の間の整数として返されます。これはPDRF 6〜10のみサポートされており、レガシーPDRF 0〜5の場合は`missing`を返します。

参照: [`PointRecord`](@ref)
