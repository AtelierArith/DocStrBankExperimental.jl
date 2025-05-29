```
primitivize(V::Union{AbstractBasis, AbstractPoint}, 
            cntr_or_sgnum::Union{Char, <:Integer})   -->  V′::typeof(V)
```

入力された従来の `AbstractBasis` または `AbstractPoint` `V` に関連付けられた原始基底または点 `V′` を返します。

想定される中心タイプは `cntr_or_sgnum` によって指定され、中心文字（`::Char`）として与えられるか、空間群番号（`::Integer`）と `V` の次元性から推測されます（詳細は [`centering(::Integer, ::Integer)`](@ref) を参照）。
