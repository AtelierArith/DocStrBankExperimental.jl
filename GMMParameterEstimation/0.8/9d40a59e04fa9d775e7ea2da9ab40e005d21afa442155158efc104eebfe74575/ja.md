```
estimate_parameters(d::Integer, k::Integer, first::Vector{Float64}, second::Matrix{Float64})
```

`d`次元のガウス`k`混合モデルのパラメータの推定値をモーメントから計算します。

未知の混合係数対角共分散行列の場合、`first`は最初の次元のモーメント0から3kのリストであり、`second`は残りの次元のモーメント1から2k+1の行列である必要があります。
