`inversions(W::FiniteCoxeterGroup, w::AbstractVector{<:Integer})`

与えられた単語 `w=[s₁,…,sₙ]`（整数のベクトル）は、要素 `W(w...)` を表し、`w` の反転を返します。つまり、`W(s₁), W(s₁,s₂,s₁), …, W(s₁,s₂,…,sₙ,sₙ₋₁,…,s₁)` によって与えられる `W` の反射のインデックスのリストです。

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> inversions(W,[2,1,2])
3-element Vector{Int64}:
 2
 4
 1
```
