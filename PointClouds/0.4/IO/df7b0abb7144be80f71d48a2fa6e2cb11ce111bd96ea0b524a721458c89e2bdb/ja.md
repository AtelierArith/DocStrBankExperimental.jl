```
source_id([T], p::PointRecord)
source_id([T], points, inds = :)
```

ポイントレコードのソースIDを取得します。これは0から65535の間の整数として定義されます。これは、同じフライトライン中に記録されたポイントをグループ化するために使用される場合があります。

参照: [`PointRecord`](@ref)
