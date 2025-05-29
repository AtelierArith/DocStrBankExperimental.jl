```
transform(k::ReciprocalPoint, P::AbstractMatrix{<:Real})  -->  k′::typeof(k)
```

逆空間の点 `k` $= (k_1, k_2, k_3)^{\text{T}}$ を変換行列 `P` $= \mathbf{P}$ の下で変換し、`k′` $= (k_1′, k_2′, k_3′)^{\text{T}} = \mathbf{P}^{\text{T}}(k_1, k_2, k_3)^{\text{T}}$ を返します。
