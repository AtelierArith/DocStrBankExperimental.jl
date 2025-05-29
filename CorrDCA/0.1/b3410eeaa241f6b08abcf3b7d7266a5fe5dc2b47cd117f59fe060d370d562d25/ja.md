```
compute_weights(Z::Matrix{Ti}, theta::Real) where Ti <: Integer
```

与えられたシーケンス `Z` からハミング距離 ≤ `theta` のシーケンスの数の正規化されたカウントを計算します。
