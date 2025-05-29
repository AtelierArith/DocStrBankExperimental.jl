```
KDEonline!{tp}(kdescores::AbstractArray{tp, 1}, x::AbstractArray{tp, 2} [, Q::AbstractArray{tp, 2}], σ::tp, dim::Int = 1)
```

xから(1.0 - カーネル密度推定)を計算し、kdescoresに書き込みます。dimは観測の次元を示します。共分散行列Qが与えられている場合、ユークリッド距離の代わりにマハラノビス距離が使用されます。
