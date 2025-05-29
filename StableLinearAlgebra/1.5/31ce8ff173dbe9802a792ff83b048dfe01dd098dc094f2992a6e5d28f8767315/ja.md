```
ldiv_lu!(A::AbstractMatrix{T}, B::AbstractMatrix{T}, ws::LUWorkspace{T}) where {T}
```

$$
B:= A^{-1} B
$$

を計算し、$B$をインプレースで修正します。行列 $A$ も上書きされます。また、$\log(|\det A^{-1}|)$ と $\textrm{sign}(\det A^{-1})$ を返します。
