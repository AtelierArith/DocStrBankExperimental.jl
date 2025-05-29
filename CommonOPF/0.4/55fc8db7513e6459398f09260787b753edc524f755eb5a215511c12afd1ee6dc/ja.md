```
kron_reduce(M::AbstractMatrix)::Matrix
```

4x4の行列が与えられたとき、4行目と4列目を削除して3x3の行列を作成します。

3x3の新しい値は次のようになります：

```julia
M_new[i,j] = M[i,j] - M[i,4] *  M[4,j] / M[4,4]  
```

ここで、`i`と`j`は`Set((1,2,3))`に含まれます。
