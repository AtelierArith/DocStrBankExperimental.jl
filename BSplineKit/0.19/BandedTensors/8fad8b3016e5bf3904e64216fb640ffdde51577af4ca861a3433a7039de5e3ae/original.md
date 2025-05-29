```
bandwidth(A::BandedTensor3D)
```

Get band width `b` of [`BandedTensor3D`](@ref).

The band width is defined here such that the element `A[i, j, k]` may be non-zero only if $|i - j| ≤ b$, $|i - k| ≤ b$ and $|j - k| ≤ b$. This definition is consistent with the specification of the upper and lower band widths in `BandedMatrices`.
