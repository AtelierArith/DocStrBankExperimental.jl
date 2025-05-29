`induced(P,S)`

は、`P` に対して `S` で誘導された部分順序集合を返します。`P` が `Poset` の場合は `P.elements` の部分リスト、`P` が `CPoset` の場合は `1:length(P)` の部分集合です。部分リスト `S` は `P.elements` と同じ順序である必要はないため、これは `P` の要素を再番号付けするために使用できます。

```julia-repl
julia> p=CPoset((i,j)->i%4<j%4,8)
4,8<1,5<2,6<3,7

julia> induced(p,2:6) # インデックスが再番号付けされる
3<4<1,5<2

julia> induced(Poset(p),2:6) # 要素が保持される
4<5<2,6<3
```
