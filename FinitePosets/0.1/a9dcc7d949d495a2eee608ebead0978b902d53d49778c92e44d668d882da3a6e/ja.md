`hasse(P::CPoset)`

`P`のハッセ図。

```julia-repl
julia> p=CPoset((i,j)->j%i==0,5)
1<3,5
1<2<4

julia> hasse(p)
5-element Vector{Vector{Int64}}:
 [2, 3, 5]
 [4]      
 []       
 []       
 []       
```

`hasse(P::Poset)`は`hasse(P.C)`を返します。
