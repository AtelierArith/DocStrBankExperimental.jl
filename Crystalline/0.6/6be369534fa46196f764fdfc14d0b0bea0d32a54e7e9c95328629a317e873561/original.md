```
transform(v::AbstractVec, P::AbstractMatrix)  -->  v′::typeof(v)
```

Return a transformed coordinate vector `v′` from an original coordinate vector `v` using a basis change matrix `P`.

Note that a basis change matrix $\mathbf{P}$ transforms direct coordinate vectors (`RVec`) as $\mathbf{r}' = \mathbf{P}^{-1}\mathbf{r}$ but transforms reciprocal coordinates (`KVec`) as $\mathbf{k}' = \mathbf{P}^{\mathrm{T}}\mathbf{k}$ [^ITA6]

[^ITA6]: M.I. Aroyo, International Tables of Crystallography, Vol. A, 6th edition (2016):      Secs. 1.5.1.2 and 1.5.2.1.
