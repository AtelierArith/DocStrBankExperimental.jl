```
pfaffian_householder(A::AbstractMatrix{T}; overwrite_a=false) where {T<:Real}
```

実数または複素数の反対称行列 A (A=-A^T) の Pfaffian を計算します。overwrite_a=true の場合、行列 A はその過程で上書きされます。この関数は Householder 三重対角化を使用します。

pfaffian*schur() 関数も実数の場合に使用できます。この関数は反対称性を利用せず、pfaffian*householder() よりもわずかに遅くなります。
