`incidence(P::CPoset)`

は `P` のインシデンス行列（ζ行列とも呼ばれる）を返します。

```julia-repl
julia> p=CPoset([i==6 ? Int[] : [i+1] for i in 1:6])
1<2<3<4<5<6

julia> incidence(p)
6×6 Matrix{Bool}:
 1  1  1  1  1  1
 0  1  1  1  1  1
 0  0  1  1  1  1
 0  0  0  1  1  1
 0  0  0  0  1  1
 0  0  0  0  0  1
```

`incidence(P::Poset)` は `incidence(P.C)` を返します。
