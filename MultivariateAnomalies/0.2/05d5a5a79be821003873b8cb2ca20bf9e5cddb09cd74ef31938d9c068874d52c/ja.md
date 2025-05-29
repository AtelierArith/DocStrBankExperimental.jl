```
REConline!{tp}(recscores::AbstractArray{tp, 1}, x::AbstractArray{tp, 2} [, Q::AbstractArray{tp, 2}], ɛ::tp, dim::Int = 1)
```

xから再帰スコアを計算し、観測の次元がdimであるrecscoresに書き込みます。共分散行列Qが与えられている場合、ユークリッド距離の代わりにマハラノビス距離が使用されます。
