```
transform(Gs::ReciprocalBasis, P::AbstractMatrix{<:Real})
```

逆基底 `Gs` $= (\mathbf{a}^* \mathbf{b}^* \mathbf{c}^*)$ を変換行列 `P` $= \mathbf{P}$ の下で変換し、`Gs′` $= (\mathbf{a}^{*\prime}\ \mathbf{b}^{*\prime}\ \mathbf{c}^{*\prime}) = (\mathbf{a}^*\ \mathbf{b}^*\ \mathbf{c}^*)(\mathbf{P}^{-1})^{\text{T}}$ を返します。
