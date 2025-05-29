`linear_extensions(P::CPoset)`

returns all linear extensions of the `CPoset` (see linear_extension)

```julia-repl
julia> p=CPoset((i,j)->j%i==0,4) # divisibility poset on 1:4
1<3
1<2<4

julia> linear_extensions(p)
3-element Vector{Vector{Int64}}:
 [1, 2, 3, 4]
 [1, 2, 4, 3]
 [1, 3, 2, 4]
```

`linear_extensions(P::Poset)` returns the linear extensions of `p.C`.
