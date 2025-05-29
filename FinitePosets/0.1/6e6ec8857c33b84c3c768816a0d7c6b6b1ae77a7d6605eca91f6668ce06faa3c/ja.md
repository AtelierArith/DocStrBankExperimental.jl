`linear_extensions(P::CPoset)`

は `CPoset` のすべての線形拡張を返します（線形拡張を参照）。

```julia-repl
julia> p=CPoset((i,j)->j%i==0,4) # 1:4 の可除性ポセット
1<3
1<2<4

julia> linear_extensions(p)
3-element Vector{Vector{Int64}}:
 [1, 2, 3, 4]
 [1, 2, 4, 3]
 [1, 3, 2, 4]
```

`linear_extensions(P::Poset)` は `p.C` の線形拡張を返します。
