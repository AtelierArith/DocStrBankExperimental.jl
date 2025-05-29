```
indices(ga::GeoArray, p::SVector{2,<:Real}, strategy::AbstractStrategy, rounding::RoundingMode)
```

座標 `p` で表されるセルの論理インデックスを取得します。`strategy` は、座標がセルの中心 (`Center`) または左上隅 (`Vertex`) を表すかを定義するために使用できます。`rounding` は、座標が最も近い整数インデックスにどのように丸められるかを定義するために使用できます。逆関数については `coords` を参照してください。
