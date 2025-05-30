```
MatDeforElastOrtho(
    mr::Type{MR},
    E1::N,
    E2::N,
    E3::N,
    nu12::N,
    nu13::N,
    nu23::N,
    G12::N,
    G13::N,
    G23::N,
) where {MR<:AbstractDeforModelRed,N<:Number}
```

弾性直交材料を作成します。

弾性特性の指定のみの便利なバージョンです。
