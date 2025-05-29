```
get_matrix(k::KernelLabel, x::AbstractArray)
```

カーネル行列 `K[i,j] = K(k.x[:,i], x[:,j])` を取得します。
