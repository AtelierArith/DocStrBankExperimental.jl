```
phi_ij(j::String, net::Network, M::AbstractMatrix)
```

行列 M を i -> j の位相でダウンセレクトし、欠落しているオフ対角位相インデックスには `0im` を、欠落している対角インデックスには `0` を格納します。
