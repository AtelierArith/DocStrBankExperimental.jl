`inversions(W::FiniteCoxeterGroup, w::AbstractVector{<:Integer})`

Given  a word `w=[s₁,…,sₙ]` (a vector of integers) representing the element `W(w...)`,  returns the inversions of  `w`, that is the  list of indices of the reflections of `W` given by `W(s₁), W(s₁,s₂,s₁), …, W(s₁,s₂,…,sₙ,sₙ₋₁,…,s₁)`.

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> inversions(W,[2,1,2])
3-element Vector{Int64}:
 2
 4
 1
```
