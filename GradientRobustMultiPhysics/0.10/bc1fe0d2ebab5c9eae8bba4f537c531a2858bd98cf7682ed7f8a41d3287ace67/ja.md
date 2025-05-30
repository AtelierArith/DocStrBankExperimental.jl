```julia
abstract type SymmetricGradient{offdiagval} <: ??
```

有限要素関数の勾配の対称部分を評価し、そのボイグト圧縮を返します（オフダイアゴナルは位置[j,k]と[k,j]で加算され、offdiagvalで重み付けされます）。
