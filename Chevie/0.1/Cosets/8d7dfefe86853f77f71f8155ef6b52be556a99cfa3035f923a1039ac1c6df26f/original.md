`twistings(W)`

`W`  should be a Coxeter group which is not a proper reflection subgroup of another reflection group (so that `inclusion(W)==eachindex(roots(W))`). The function returns all `spets` representing twisted forms of algebraic groups of type `W`.

```julia-repl
julia> twistings(coxgroup(:A,3)*coxgroup(:A,3))
8-element Vector{Spets{FiniteCoxeterGroup{Perm{Int16},Int64}}}:
 A₃×A₃
 A₃×²A₃
 ²A₃×A₃
 ²A₃×²A₃
 (A₃A₃)
 ²(A₃A₃)
 ²(A₃A₃)₍₁₂₃₆₅₄₎
 (A₃A₃)₍₁₂₃₆₅₄₎

julia> twistings(coxgroup(:D,4))
6-element Vector{Spets{FiniteCoxeterGroup{Perm{Int16},Int64}}}:
 D₄
 ²D₄₍₂₄₃₁₎
 ²D₄
 ³D₄
 ²D₄₍₁₄₃₂₎
 ³D₄₍₁₄₃₂₎

julia> W=rootdatum(:so,8)
so₈

julia> twistings(W)
2-element Vector{Spets{FiniteCoxeterGroup{Perm{Int16},Int64}}}:
 D₄
 ²D₄

```
