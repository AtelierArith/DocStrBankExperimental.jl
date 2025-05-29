`elements(M::LocallyGarsideMonoid,l::Integer)` `elements(M::LocallyGarsideMonoid,v::AbstractVector{<:Integer})`

`M` は加法的長さ関数を持っている必要があります（つまり、`l` 個の原子の積は、`l` 未満の原子の積とは等しくありません）。`elements(M,l)` は、`M` における長さ `l` の要素のリストを返します。

第二の形式では、`elements` は `i∈ v` のすべての長さ `i` の要素を返します。

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
