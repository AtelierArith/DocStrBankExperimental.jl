```
estimate_parameters(d::Integer, k::Integer, first::Vector{Float64}, second::Matrix{Float64}, last::Dict{Vector{Int64}, Float64}; method = "recursive")
```

`d`次元ガウス`k`混合モデルのパラメータの推定値をモーメントから計算します。

未知の混合係数一般共分散行列の場合、`first`は最初の次元のモーメント0から3kのリストである必要があり、`second`は残りの次元のモーメント1から2k+1の行列であり、`last`は整数のリストとしてのインデックスと対応するモーメントの辞書である必要があります。
