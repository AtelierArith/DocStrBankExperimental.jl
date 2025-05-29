`elements(M::LocallyGarsideMonoid,l::Integer)` `elements(M::LocallyGarsideMonoid,v::AbstractVector{<:Integer})`

`M`  should have  an additive  length function  (that is,  a product of `l` atoms  is not equal to any product of less than `l` atoms). `elements(M,l)` returns the list of elements of length `l` in `M`.

In the second form `elements` returns all elements of length `i` for `i∈ v`.

```julia-repl
julia> M=BraidMonoid(coxgroup(:A,2))
BraidMonoid(A₂)

julia> elements(M,4)
12-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}:
 Δ.1
 Δ.2
 12.21
 12.2.2
 1.12.2
 1.1.12
 1.1.1.1
 21.12
 21.1.1
 2.21.1
 2.2.21
 2.2.2.2
```
