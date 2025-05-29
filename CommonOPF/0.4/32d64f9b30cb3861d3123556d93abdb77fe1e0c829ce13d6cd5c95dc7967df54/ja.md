```
phi_ij(j::String, net::Network, v::AbstractVector)
```

i -> j の位相によってベクトル v を選択し、欠落している位相インデックスには `0im` を格納します。
