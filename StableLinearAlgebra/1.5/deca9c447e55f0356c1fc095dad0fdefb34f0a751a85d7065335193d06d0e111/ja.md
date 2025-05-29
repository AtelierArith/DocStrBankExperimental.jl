```
det_lu!(A::AbstractMatrix{T}, ws::LUWorkspace{T}) where {T}
```

返す $\log(|\det A|)$ と $\textrm{sign}(\det A).$ 注意してください、この関数によって $A$ は左側が修正されます。
