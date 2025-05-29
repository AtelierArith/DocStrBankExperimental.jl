```julia
perp(S::Subspaces.Subspace) -> Subspaces.Subspace

```

直交部分空間を返します。`~S`としても書くことができます。

```jldoctest
julia> S = Subspace([ [1,2,3], [4,5,6] ])
Subspace{Float64} size (3,) dim 2

julia> perp(S)
Subspace{Float64} size (3,) dim 1

julia> perp(S) == ~S
true

julia> perp(S) ⟂ S
true
```
