```
estimate_parameters(k::Integer, shared_cov::Matrix{Float64}, first::Vector{Float64}, second::Matrix{Float64}; method = "recursive")
```

ガウスの `k`-混合モデルの平均の推定値を、等しい混合係数と既知の共有共分散からモーメントを用いて計算します。

共有共分散行列 `shared_cov` は次元を決定します。次に、`first` は最初の次元のモーメント 0 から k までのリストである必要があります。`second` は、j が 0 から `k`-1 まで、i が 2 から d までのモーメント $m_{je_1+e_i}$ の行列であり、ここで d は次元であり、i は行を横断し、j は列を下に変化させます。
