`torus(W,i)`

ここで `W` は `Spets` または `ComplexReflectionGroup` です。これは、`W` の `i` 番目の共役類の代表によってねじれたトーラスを返します。これは `twistings(W,Int[])[i]` と同じです。

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> twistings(W,Int[])
5-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 A₃₍₎=Φ₁³
 A₃₍₎=Φ₁²Φ₂
 A₃₍₎=Φ₁Φ₂²
 A₃₍₎=Φ₁Φ₃
 A₃₍₎=Φ₂Φ₄

julia> torus(W,2)
A₃₍₎=Φ₁²Φ₂

julia> WF=spets(W,Perm(1,3))
²A₃

julia> twistings(WF,Int[])
5-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 ²A₃₍₎=Φ₂³
 ²A₃₍₎=Φ₁Φ₂²
 ²A₃₍₎=Φ₁²Φ₂
 ²A₃₍₎=Φ₂Φ₆
 ²A₃₍₎=Φ₁Φ₄

julia> torus(WF,2)
²A₃₍₎=Φ₁Φ₂²
```
