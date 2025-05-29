`linear_extension(P::CPoset)`

は `CPoset` の線形拡張を返します。これは、整数 `1:length(P)` の順列を含むベクトル `l` であり、もし `P` において `i<j` であれば（すなわち `incidence(P)[i,j]` が `true` であれば）、`l` において `i` は `j` の前にあります。これは `P` のトポロジカルソートとも呼ばれます。

```julia-repl
julia> p=CPoset((i,j)->j%i==0,6) # 1:6 の可除性ポセット
1<5
1<2<4
1<3<6
2<6

julia> linear_extension(p)
6-element Vector{Int64}:
 1
 2
 3
 5
 4
 6
```

`linear_extension(P::Poset)` は `P.C` の線形拡張を返します。
