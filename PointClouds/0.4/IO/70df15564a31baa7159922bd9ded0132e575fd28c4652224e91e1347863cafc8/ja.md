```
extra_bytes(p::PointRecord)
extra_bytes(points, inds = :)
```

ポイントレコードの「追加バイト」を `UInt8` のタプルとして取得します。これらのバイトの意味は可変長レコードで説明される場合があります。

参照: [`PointRecord`](@ref), [`user_data`](@ref)
