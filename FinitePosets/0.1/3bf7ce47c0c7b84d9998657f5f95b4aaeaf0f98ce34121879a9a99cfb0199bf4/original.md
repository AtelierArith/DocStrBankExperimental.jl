`linear_extension(P::CPoset)`

returns a linear extension of the `CPoset`, that is a vector `l` containing a permutation of the integers `1:length(P)` such that if `i<j` in `P` (that is  `incidence(P)[i,j]` is `true`), then `i` is  before `j` in `l`. This is also called a topological sort of `P`.

```julia-repl
julia> p=CPoset((i,j)->j%i==0,6) # divisibility poset on 1:6
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

`linear_extension(P::Poset)` returns a linear extension of `P.C`.
