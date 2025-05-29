`FamiliesClassical(l)`

`l` は、`Bᵣ` または `Cᵣ` 型のための `symbols(2,r)` のように、古典的な冪零群のキャラクターを分類するシンボルのリストである必要があります。また、`Dᵣ` 型のための `symbols(2,r,0)` のようにすることもできます。この関数は、これらのシンボルによって決定されるファミリーのリストを返します。

```julia-repl
julia> FamiliesClassical(symbols(2,3)) # B₃ 型の冪零群の場合
6-element Vector{Family}:
 Family(112,[2])
 Family(022,[6])
 Family(3,[9])
 Family(01123,[1, 3, 8, 11])
 Family(0112233,[4])
 Family(013,[5, 7, 10, 12])
```
