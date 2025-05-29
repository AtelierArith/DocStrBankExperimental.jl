```
spread(points::Matrix{<:Real}, initial::Matrix{<:Real}, friction::Real; distance=Euclidean(), res=1.0)
spread(points::Matrix{<:Real}, initial::Real, friction::Real; distance=Euclidean(), res=1.0)
```

最適化された（より正確な）関数で、どこでも同じ摩擦に基づいています。

摩擦がどこでも同じであれば、最短コストパスを探す必要はなく、入力ポイントに直接線を引くだけで済みます。

計算されたコストはより正確で、セルの中心からセルの中心への「ジグザグ」がありません。
