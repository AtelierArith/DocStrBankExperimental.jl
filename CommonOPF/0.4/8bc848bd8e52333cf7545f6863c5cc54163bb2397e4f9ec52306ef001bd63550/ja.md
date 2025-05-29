```
bij_per_unit(i::AbstractString, j::AbstractString, net::Network)

susceptance(net[(i,j)]) * net.Zbase
```

エッジ i-j の感受性を `net.Zbase` で正規化したもの
