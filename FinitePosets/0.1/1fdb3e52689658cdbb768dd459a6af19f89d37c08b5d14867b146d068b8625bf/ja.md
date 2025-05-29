`is_meet_semilattice(P)` で `P` が `Poset` または `CPoset` の場合

`P` が合併半格である場合に限り `true` を返します。つまり、`P` の任意の2つの要素は一意の最大下界を持ちます。そうでない場合は `false` を返します。

```julia-repl
julia> p=CPoset((i,j)->j%i==0,8)
1<5,7
1<2<4<8
1<3<6
2<6

julia> is_meet_semilattice(p)
true
```
