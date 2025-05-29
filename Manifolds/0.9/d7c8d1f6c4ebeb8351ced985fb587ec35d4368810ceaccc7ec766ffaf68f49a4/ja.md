```
Y = project(M::SPDFixedDeterminant, p, X)
project!(M::SPDFixedDeterminant, Y, p, X)
```

対称行列 `X` を、行列式 `M.d` の s.p.d. 行列の（部分）多様体の点 `p` での接空間に射影します（`Y` の代わりに）。対角成分（したがってトレース）をゼロに設定することによって行います。
