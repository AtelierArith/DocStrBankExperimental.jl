```
inv_lu!(A::AbstractMatrix{T}, ws::LUWorkspace{T}) where {T}
```

Calculate the inverse of the matrix `A`, overwriting `A` in-place. Also return $\log(|\det A^{-1}|)$ and $\textrm{sign}(\det A^{-1}).$
