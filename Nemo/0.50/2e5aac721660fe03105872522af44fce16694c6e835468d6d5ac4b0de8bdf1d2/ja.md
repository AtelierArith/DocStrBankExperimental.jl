```
snf_with_transform(A::ZZMatrix, l::Bool = true, r::Bool = true) -> ZZMatrix, ZZMatrix, ZZMatrix
```

整数行列 $A$ が与えられたとき、$A$ のスミス正規形（基本因子正規形）を計算します。`l` および/または `r` が true の場合、対応する左および/または右の変換行列も計算されます。
