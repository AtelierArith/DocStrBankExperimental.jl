```
normalize1!(B::AbstractArray{<:Real}, A::AbstractArray{<:Real})
```

`A`の値を正規化して`sum(B) ≈ 1`となるようにし、`0 ≤ B[i] ≤ 1` ∀iを満たすようにし、結果を`B`に格納します。`A[i] ≥ 0` ∀iであると仮定します。
