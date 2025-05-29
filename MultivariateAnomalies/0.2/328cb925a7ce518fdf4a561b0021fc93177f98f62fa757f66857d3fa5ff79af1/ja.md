```
KNNonline!{tp}(knnscores::AbstractArray{tp, 1}, x::AbstractArray{tp, 2}, [Q::AbstractArray{tp, 2},] k::Int, dim::Int = 1)
```

xからk近傍（ガンマ）スコアを計算し、knnscoresに書き込みます。dimは観測の次元を示します。共分散行列Qが与えられた場合、ユークリッド距離の代わりにマハラノビス距離が使用されます。
