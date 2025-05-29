```
transform(k::ReciprocalPoint, P::AbstractMatrix{<:Real})  -->  k′::typeof(k)
```

Transform a point in reciprocal space `k` $= (k_1, k_2, k_3)^{\text{T}}$ under the transformation matrix `P` $= \mathbf{P}$, returning `k′` $= (k_1′, k_2′, k_3′)^{\text{T}} = \mathbf{P}^{\text{T}}(k_1, k_2, k_3)^{\text{T}}$.
