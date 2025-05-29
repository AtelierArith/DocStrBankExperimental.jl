```
pfaffian(A::AbstractMatrix{T}, overwrite_a=false, method='P') where {T<:Number}
```

実数または複素数の反対称行列 A (A=-A^T) の Pfaffian を計算します。overwrite_a=true の場合、行列 A はその過程で上書きされます。この関数は、Parlett-Reid アルゴリズム (method='P', デフォルト) または Householder 三重対角化 (method='H') のいずれかを使用します。
