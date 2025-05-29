```
struct ToTolerance{T<:Coordinate} <: GeometryEntityStyle
    atol::T
end
```

エンティティを絶対許容誤差 `atol` でレンダリングするためのスタイル。

このエンティティをレンダリングする際にキーワード `atol` を渡すか上書きすることと同等です。
