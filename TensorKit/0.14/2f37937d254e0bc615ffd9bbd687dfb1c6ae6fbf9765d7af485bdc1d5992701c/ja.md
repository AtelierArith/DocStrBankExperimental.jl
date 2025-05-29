```
insertleftunit(W::HomSpace, i=numind(W) + 1; conj=false, dual=false)
```

位置 `i` に、基礎となる体に同型の自明なベクトル空間を挿入します。`Int` または `Val(i)` として指定でき、型の安定性が向上します。より具体的には、左のモノイダル単位またはその双対を追加します。

他にも [`insertrightunit`](@ref insertrightunit(::HomSpace, ::Val{i}) where {i}), [`removeunit`](@ref removeunit(::HomSpace, ::Val{i}) where {i}) を参照してください。
