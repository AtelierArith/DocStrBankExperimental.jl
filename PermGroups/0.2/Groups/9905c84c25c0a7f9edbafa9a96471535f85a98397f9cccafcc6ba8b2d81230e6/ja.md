`transversal(G::Group,p,action::Function=^)`

は、`OrderedDict` `t` を返します。キーは `orbit(G,p,action)` であり、`t[x]` は `G` の要素で、`x==action(p,t[x])` となるようなものです。したがって、`orbit` と同様に、`p` の型はハッシュ可能である必要があります。

```julia-repl
julia> G=Group(Perm(1,2),Perm(2,3));
julia> transversal(G,1)
OrderedDict{Int64, Perm{Int16}} with 3 entries:
  1 => ()
  2 => (1,2)
  3 => (1,3,2)
```

orbit 関数は、キーワード引数として `G` の任意のアクションを受け取ることができます。

```julia-repl
julia> transversal(G,(1,2),ontuples)
OrderedDict{Tuple{Int64, Int64}, Perm{Int16}} with 6 entries:
  (1, 2) => ()
  (2, 1) => (1,2)
  (1, 3) => (2,3)
  (3, 1) => (1,3,2)
  (2, 3) => (1,2,3)
  (3, 2) => (1,3)
```
