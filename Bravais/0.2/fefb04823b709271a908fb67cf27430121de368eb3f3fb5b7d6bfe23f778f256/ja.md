```
transform(r::DirectPoint, P::AbstractMatrix{<:Real})  -->  r′::typeof(r)
```

直接空間の点 `r` $= (r_1, r_2, r_3)^{\text{T}}$ を変換行列 `P` $= \mathbf{P}$ の下で変換し、`r′` $= (r_1′, r_2′, r_3′)^{\text{T}} = \mathbf{P}^{-1}(r_1, r_2, r_3)^{\text{T}}$ を返します。
