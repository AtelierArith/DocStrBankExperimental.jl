```
orth_projection(v::AbstractVector, basis::AbstractMatrix, args...) -> AbstractVector
```

ベクトル `v` を基底 `basis` の列空間に直交射影します。対称かつ正定値の行列 `X` が引数として提供されると、出力は `X`-直交になります。それ以外の場合は ℓ²-直交です。
