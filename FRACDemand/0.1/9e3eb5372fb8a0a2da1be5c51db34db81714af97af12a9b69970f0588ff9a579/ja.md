```
`HaltonDraws!{T<:AbstractFloat}(H::Vector{T}, B::Int, [skip::Int=500, distr=Normal()])`
```

古いバージョンのHalton.jlからコピーされました。`H`を分布`Distributions.dist()`からのサンプルで置き換えます。サンプルは、基数`B`を量子として使用してHalton列を用いて生成されます。キーワード引数`skip`は、ドロップする初期の「バーニングイン」要素の数です。
