```
user_data([T], p::PointRecord)
user_data([T], points, inds = :)
```

ポイントレコードの「ユーザーデータ」を取得します。これは0から255の間の整数として定義されています。このデータはすべてのPDRFに含まれていますが、標準化された意味はありません。

参照: [`PointRecord`](@ref), [`extra_bytes`](@ref)
