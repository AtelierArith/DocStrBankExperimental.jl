`is_join_semilattice(P::CPoset)` where `P` is a `Poset` or `CPoset`

returns  `true` iff `P` is a join  semilattice, that is any two elements of `P` have a unique smallest upper bound; returns `false` otherwise.

```julia-repl
julia> p=CPoset((i,j)->j%i==0,8)
1<5,7
1<2<4<8
1<3<6
2<6

julia> is_join_semilattice(p)
false
```
