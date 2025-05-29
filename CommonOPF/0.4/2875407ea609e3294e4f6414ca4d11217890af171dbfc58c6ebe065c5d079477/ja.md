```
rij_per_unit(i::AbstractString, j::AbstractString, net::Network)

resistance(net[(i,j)]) / net.Zbase
```

エッジ i-j の抵抗を `net.Zbase` で正規化したもの
