```
box() = BOX
box(r::AbstractRelation) = BoxRelationalConnective(r)
```

ボックスモーダル接続詞（すなわち、□）を返すか、関係 `r` をラップしたマルチモーダル論理のボックス関係接続詞を返します。

詳細は [`BoxRelationalConnective`](@ref)、[`box`](@ref)、[`BOX`](@ref) を参照してください。
