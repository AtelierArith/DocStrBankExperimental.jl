`CPoset(f::Function,n::integer)`

creates the `Poset` on `1:n` with order given by function `f`.

```julia-repl
julia> CPoset((x,y)->y%x==0,8)  # the divisibility poset
1<5,7
1<2<4<8
1<3<6
2<6
```
