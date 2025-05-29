```
ldiv_lu!(A::AbstractMatrix{T}, B::AbstractMatrix{T}, ws::LUWorkspace{T}) where {T}
```

Calculate $B:= A^{-1} B,$ modifying $B$ in-place. The matrix $A$ is over-written as well. Also return $\log(|\det A^{-1}|)$ and $\textrm{sign}(\det A^{-1}).$
