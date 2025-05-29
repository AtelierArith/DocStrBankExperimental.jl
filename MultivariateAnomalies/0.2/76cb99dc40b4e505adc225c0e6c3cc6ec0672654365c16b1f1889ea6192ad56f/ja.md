```
Euclidean_distance!{tp}(d::Array{tp, 1}, x::AbstractArray{tp, 2}, i::Int, j::Int, dim::Int = 1)
```

x[i,:] と x[j,:] の間のユークリッド距離を計算し、その結果を d に書き込みます。メモリ効率が良いです。dim は i と j の次元です。
