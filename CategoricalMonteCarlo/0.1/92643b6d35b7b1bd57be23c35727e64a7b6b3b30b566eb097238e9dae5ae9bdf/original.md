```
normalize1!(B::AbstractArray{<:Real}, A::AbstractArray{<:Real})
```

Normalize the values in `A` such that `sum(B) ≈ 1` and `0 ≤ B[i] ≤ 1` ∀i, storing the result in `B`. It is assumed that `A[i] ≥ 0` ∀i.
