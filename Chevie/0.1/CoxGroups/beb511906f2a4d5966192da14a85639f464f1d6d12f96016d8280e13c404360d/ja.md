`reduced(W,w)`

コセット W.w における最小長のユニークな要素。これは `isleftdescent(W,u)` が `u∈ W.w` に対して意味を持つときに意味があります。これは `w` が `W` のコクセター自己同型であるか、または `w` が `W` のコクセター超群に存在する場合に発生します。

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
