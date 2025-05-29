```
transform(Gs::ReciprocalBasis, P::AbstractMatrix{<:Real})
```

Transform a reciprocal basis `Gs` $= (\mathbf{a}^* \mathbf{b}^* \mathbf{c}^*)$ under the transformation matrix `P` $= \mathbf{P}$, returning  `Gs′` $= (\mathbf{a}^{*\prime}\ \mathbf{b}^{*\prime}\ \mathbf{c}^{*\prime}) = (\mathbf{a}^*\ \mathbf{b}^*\ \mathbf{c}^*)(\mathbf{P}^{-1})^{\text{T}}$.
