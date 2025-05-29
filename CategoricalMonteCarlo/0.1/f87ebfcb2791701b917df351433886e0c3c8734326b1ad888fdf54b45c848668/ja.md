```
normalize1(A::AbstractArray{<:Real})
```

サイズが等しい配列を返し、`sum(B) ≈ 1` および `0 ≤ B[i] 1` ∀i を満たします。`A[i] ≥ 0` ∀i であると仮定します。

関連情報: [`normalize1!`](@ref)
