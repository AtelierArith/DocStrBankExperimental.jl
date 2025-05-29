```
wrap(x, xref, unit_cell_matrix::SMatrix{N,N,T}) where {N,T}
wrap(x, xref, sides::AbstractVector)
```

点 `x` の座標を `xref` に対して最小画像となるようにラップします。単位セルは、サイズ `(N,N)` の静的行列または長さ `N` のベクトルとして与えることができます。
