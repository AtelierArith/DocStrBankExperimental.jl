```
conventionalize(V′::Union{AbstractBasis, AbstractPoint}, 
                cntr_or_sgnum::Union{Char, <:Integer})    -->  V::typeof(V′)
```

入力された原始 `AbstractBasis` または `AbstractPoint` `V′` に関連付けられた従来の基底または点 `V` を返します。

想定される中心化タイプは `cntr_or_sgnum` によって指定され、中心化文字 (`::Char`) として与えられるか、空間群番号 (`::Integer`) と `V′` の次元性から推測されます（詳細は [`centering(::Integer, ::Integer)`](@ref) を参照）。
