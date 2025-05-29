`reduced(W,w)`

The  unique element of  minimal length in  the coset W.w.  This makes sense when  `isleftdescent(W,u)` makes sense for `u∈  W.w` which happens when `w` is  a Coxeter automorphism of `W` or  when `w` lives in a Coxeter overgroup of `W`.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> H=reflection_subgroup(W,[2,6])
G₂₍₂₆₎=Ã₁×A₁

julia> word.(Ref(W),unique(reduced.(Ref(H),elements(W))))
3-element Vector{Vector{Int64}}:
 []
 [1]
 [1, 2]
```
