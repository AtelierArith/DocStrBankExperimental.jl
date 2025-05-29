```
insertleftunit(tsrc::AbstractTensorMap, i=numind(t) + 1;
               conj=false, dual=false, copy=false) -> tdst
```

位置 `i` に、基底体に同型の自明なベクトル空間を挿入します。`i` は `Int` または型の安定性を向上させるために `Val(i)` として指定できます。より具体的には、左のモノイダル単位またはその双対を追加します。

`copy=false` の場合、`tdst` は可能な限り `tsrc` とデータを共有することがあります。そうでない場合、常にコピーが作成されます。

他にも [`insertrightunit`](@ref insertrightunit(::AbstractTensorMap, ::Val{i}) where {i})、[`removeunit`](@ref removeunit(::AbstractTensorMap, ::Val{i}) where {i}) を参照してください。
