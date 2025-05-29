```
inv_lu!(A::AbstractMatrix{T}, ws::LUWorkspace{T}) where {T}
```

行列 `A` の逆行列を計算し、`A` をその場で上書きします。また、$\log(|\det A^{-1}|)$ と $\textrm{sign}(\det A^{-1})$ を返します。
