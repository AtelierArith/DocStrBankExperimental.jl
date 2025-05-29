```
estimate_parameters_weights_known(d::Integer, k::Integer, w::Array{Float64}, first::Matrix{Float64}, last::Dict{Vector{Int64}, Float64}; method = "recursive")
```

`d`次元のガウス`k`混合モデルのパラメータをモーメントから推定します。

混合係数が既知の一般的な共分散行列の場合、`w`は混合係数のベクトルであり、`first`は最初の次元のモーメント0から3kのリスト、`second`は残りの次元のモーメント1から2k+1の行列、`last`は整数のリストとしてのインデックスと対応するモーメントの辞書である必要があります。
