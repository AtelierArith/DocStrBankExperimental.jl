`stabilizer(G::Group,s,action=^)`

は、`action(p,g)==p` となる `G` の要素 `g` の部分群を計算します。

```julia-repl
julia> G=Group(Perm(1,2),Perm(1,2,3,4))
Group((1,2),(1,2,3,4))
```

`s` は重複のないソートされたリストとして表される集合であると仮定します。`onsets` は、`g∈ G` によって与えられるアクションで、`(g,p)->sort(p.^g)` です。

```julia-repl
julia> stabilizer(G,[1,2],onsets)
Group((3,4),(1,2))
```
