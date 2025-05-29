```
insertrightunit(tsrc::AbstractTensorMap, i=numind(t);
                conj=false, dual=false, copy=false) -> tdst
```

位置 `i` の後に、基礎となる体に同型の自明なベクトル空間を挿入します。`i` は `Int` または型の安定性を向上させるために `Val(i)` として指定できます。より具体的には、右モノイダル単位またはその双対を追加します。

`copy=false` の場合、`tdst` は可能な限り `tsrc` とデータを共有することがあります。そうでない場合は、常にコピーが作成されます。

[`insertleftunit`](@ref insertleftunit(::AbstractTensorMap, ::Val{i}) where {i})、[`removeunit`](@ref removeunit(::AbstractTensorMap, ::Val{i}) where {i}) も参照してください。
