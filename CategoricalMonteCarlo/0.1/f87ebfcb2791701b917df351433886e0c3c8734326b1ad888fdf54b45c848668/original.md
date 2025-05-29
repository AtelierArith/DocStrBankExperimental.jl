```
normalize1(A::AbstractArray{<:Real})
```

Return an array of equal size which satisfies `sum(B) ≈ 1` and `0 ≤ B[i] 1` ∀i. It is assumed that `A[i] ≥ 0` ∀i.

See also: [`normalize1!`](@ref)
