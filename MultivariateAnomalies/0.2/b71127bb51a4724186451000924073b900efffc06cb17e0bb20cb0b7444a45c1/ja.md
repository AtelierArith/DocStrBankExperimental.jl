```
SigmaOnline!{tp}(sigma::Array{tp, 1}, x::AbstractArray{tp, 2}, [Q::AbstractArray{tp, 2}], samplesize::Int = 250, dim::Int = 1)
```

`sigma` パラメータを `dim` に沿った `samplesize` のランダムにサンプリングされた点の距離の平均として計算します。Q が指定されている場合、ユークリッド距離の代わりにマハラノビス距離が使用されます。
