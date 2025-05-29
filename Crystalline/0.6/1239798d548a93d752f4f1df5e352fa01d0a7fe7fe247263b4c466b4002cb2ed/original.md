```
primitivize(v::AbstractVec, cntr::Char)  -->  v′::typeof(v)
```

Transforms a conventional coordinate vector `v` to a standard primitive basis (specified by the centering type `cntr`), returning the primitive coordinate vector `v′`.

Note that a basis change matrix $\mathbf{P}$ (as returned e.g. by [`Bravais.primitivebasismatrix`](@ref)) transforms direct coordinate vectors ([`RVec`](@ref)) as $\mathbf{r}' = \mathbf{P}^{-1}\mathbf{r}$ but transforms reciprocal coordinates ([`KVec`](@ref)) as $\mathbf{k}' = \mathbf{P}^{\text{T}}\mathbf{k}$ [^ITA6]. Recall also the distinction between transforming a basis and the coordinates of a vector.

[^ITA6]: M.I. Aroyo, International Tables of Crystallography, Vol. A, 6th edition (2016):      Secs. 1.5.1.2 and 1.5.2.1.
