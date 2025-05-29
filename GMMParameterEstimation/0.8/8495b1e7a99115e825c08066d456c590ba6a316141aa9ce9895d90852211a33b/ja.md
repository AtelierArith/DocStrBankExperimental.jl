```
estimate_parameters_weights_known(d::Integer, k::Integer, w::Array{Float64}, moments::Matrix{Float64})
```

`d`次元のガウス`k`混合モデルのパラメータをモーメントから推定します。

既知の混合係数対角共分散行列の場合、`w`は混合係数のベクトルであり、`moments`はすべての次元に対して1から2k+1までのモーメントの行列である必要があります。
