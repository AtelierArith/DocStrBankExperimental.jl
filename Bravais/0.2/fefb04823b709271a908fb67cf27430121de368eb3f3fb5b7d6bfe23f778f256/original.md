```
transform(r::DirectPoint, P::AbstractMatrix{<:Real})  -->  r′::typeof(r)
```

Transform a point in direct space `r` $= (r_1, r_2, r_3)^{\text{T}}$ under the transformation matrix `P` $= \mathbf{P}$, returning `r′` $= (r_1′, r_2′, r_3′)^{\text{T}} = \mathbf{P}^{-1}(r_1, r_2, r_3)^{\text{T}}$.
