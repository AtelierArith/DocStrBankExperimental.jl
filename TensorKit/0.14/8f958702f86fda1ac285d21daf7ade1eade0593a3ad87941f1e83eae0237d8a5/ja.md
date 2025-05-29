```
insertrightunit(W::HomSpace, i=numind(W); conj=false, dual=false)
```

位置 `i` の後に、基礎となる体に同型の自明なベクトル空間を挿入します。`Int` または型の安定性を向上させるために `Val(i)` として指定できます。より具体的には、右モノイダル単位またはその双対を追加します。

関連情報として [`insertleftunit`](@ref insertleftunit(::HomSpace, ::Val{i}) where {i}), [`removeunit`](@ref removeunit(::HomSpace, ::Val{i}) where {i}) を参照してください。
