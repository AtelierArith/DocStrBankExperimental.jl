`induced(P,S)`

returns the subposet induced by `P` on `S`, a sublist of `P.elements` if `P isa  Poset` or a subset  of `1:length(P)` if `P  isa CPoset`. Note that the sublist  `S` does not have to be in the same order as `P.elements`, so this can be just used to renumber the elements of `P`.

```julia-repl
julia> p=CPoset((i,j)->i%4<j%4,8)
4,8<1,5<2,6<3,7

julia> induced(p,2:6) # indices are renumbered
3<4<1,5<2

julia> induced(Poset(p),2:6) # elements are kept
4<5<2,6<3
```
