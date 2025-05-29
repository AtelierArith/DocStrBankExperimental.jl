`is_join_semilattice(P::CPoset)` で `P` は `Poset` または `CPoset` です。

`P` が結合半格である場合に `true` を返します。つまり、`P` の任意の2つの要素は一意の最小上限を持ちます。そうでない場合は `false` を返します。

```julia-repl
julia> p=CPoset((i,j)->j%i==0,8)
1<5,7
1<2<4<8
1<3<6
2<6

julia> is_join_semilattice(p)
false
```
