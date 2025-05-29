```
 inducingpoints([rng::AbstractRNG], alg::Greedy, X::AbstractVector; 
    y::AbstractVector, kernel::Kernel, noise::Real)
 inducingpoints([rng::AbstractRNG], alg::Greedy, X::AbstractMatrix; 
    obsdim=1, y::AbstractVector, kernel::Kernel, noise::Real)
```

Greedyアルゴリズムを使用して誘導点を選択します。追加のキーワード引数として出力 `y`、`kernel`、および `noise` が必要です。
