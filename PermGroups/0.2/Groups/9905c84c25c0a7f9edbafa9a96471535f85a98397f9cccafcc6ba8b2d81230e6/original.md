`transversal(G::Group,p,action::Function=^)`

returns  an `OrderedDict` `t` with keys  `orbit(G,p,action)` and where `t[x]` is an element  of  `G`  such  that  `x==action(p,t[x])`.  Like  `orbit`,  it thus requires the type of `p` to be hashable.

```julia-repl
julia> G=Group(Perm(1,2),Perm(2,3));
julia> transversal(G,1)
OrderedDict{Int64, Perm{Int16}} with 3 entries:
  1 => ()
  2 => (1,2)
  3 => (1,3,2)
```

orbit functions can take any action of `G` as keyword argument

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
