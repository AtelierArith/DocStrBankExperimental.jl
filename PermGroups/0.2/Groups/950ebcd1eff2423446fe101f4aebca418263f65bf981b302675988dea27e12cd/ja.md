`centralizer(G::Group,p,action=^)`

は、`action(p,g)==p` を満たす `G` の要素 `g` の部分群を計算します。

```julia-repl
julia> G=Group(Perm(1,2),Perm(1,2,3));
julia> centralizer(G,1)
Group((2,3))
```
