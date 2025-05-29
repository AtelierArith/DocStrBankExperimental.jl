```
insertrightunit(P::ProductSpace, i=lenght(P); conj=false, dual=false)
```

位置 `i` の後に、基礎となる体に同型の自明なベクトル空間を挿入します。`Int` または `Val(i)` として指定でき、型の安定性が向上します。より具体的には、右モノイダル単位またはその双対を追加します。

関連情報として [`insertleftunit`](@ref insertleftunit(::ProductSpace, ::Val{i}) where {i}), [`removeunit`](@ref removeunit(::ProductSpace, ::Val{i}) where {i}) を参照してください。
