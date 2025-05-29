`bruhatPoset(W::CoxeterGroup,w=longest(W))`

は、`W`のBruhat区間 `[1,w]` を順序集合として返します。`w` が指定されていない場合、`W` の全体のBruhat順序集合が返されます（この場合、`W` は有限でなければなりません）。

```julia-repl
julia> W=coxsym(3)
𝔖 ₃

julia> bruhatPoset(W)
.<1,2<21,12<121
```

上記の順序集合は、Hasse図を効率的に構築することによって構築されますが、次のように単純に構築することもできます。

```julia-repl
julia> p=Poset((x,y)->bruhatless(W,x,y),elements(W))
()<(1,2),(2,3)<(1,3,2),(1,2,3)<(1,3)
```

出力はあまり見栄えが良くなく、単語の代わりに順列が表示されます。これは次のように定義することで修正できます。

```julia-repl
julia> p.show_element=(io,x,n)->join(io,word(W,x.elements[n]));

julia> p
<1,2<12,21<121

julia> W=coxsym(4)
𝔖 ₄

julia> bruhatPoset(W,W(1,3))
.<3,1<13
```
