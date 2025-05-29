```
box() = BOX
box(r::AbstractRelation) = BoxRelationalConnective(r)
```

単一モーダル論理からのボックスモーダル接続詞（すなわち、□）を返すか、関係 `r` をラップした多モーダル論理からのボックス関係接続詞を返します。

詳細は [`BoxRelationalConnective`](@ref)、[`box`](@ref)、[`BOX`](@ref) を参照してください。
