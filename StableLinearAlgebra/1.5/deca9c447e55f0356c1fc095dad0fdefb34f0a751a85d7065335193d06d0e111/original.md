```
det_lu!(A::AbstractMatrix{T}, ws::LUWorkspace{T}) where {T}
```

Return $\log(|\det A|)$ and $\textrm{sign}(\det A).$ Note that $A$ is left modified by this function.
