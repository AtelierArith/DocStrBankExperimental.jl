```
diamond() = DIAMOND
diamond(r::AbstractRelation) = DiamondRelationalConnective(r)
```

単一モーダル論理からのダイヤモンドモーダル接続詞（すなわち、◊）または、関係 `r` をラップした多モーダル論理からのダイヤモンド関係接続詞を返します。

[`DiamondRelationalConnective`](@ref)、[`diamond`](@ref)、[`DIAMOND`](@ref)も参照してください。
