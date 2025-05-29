`Hom(S::Group,T::Group,images)`

は、`S` から `T` へのホモモルフィズムを表すオブジェクトを構築し、`gens(S)` を `images` にマッピングします。

```julia-repl
julia> S=Group(Perm(1,2),Perm(2,3))
Group((1,2),(2,3))

julia> T=Group(Perm(1,2))
Group((1,2))

julia> h=Hom(S,T,[T(1),T(1)])
Hom(Group((1,2),(2,3))→ Group((1,2));[(1,2), (2,3)]↦ [(1,2), (1,2)]

julia> h(S(1,2)) # h による像
()
```
