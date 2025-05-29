```
 inducingpoints([rng::AbstractRNG], alg::RandomSubset, X::AbstractVector; [weights::Vector=nothing])
 inducingpoints([rng::AbstractRNG], alg::RandomSubset, X::AbstractMatrix; obsdim=1, [weights::Vector=nothing])
```

ランダムサブセットを使用して誘導点を選択します。オプションで、入力 `X` のための重みベクトルを受け入れます。
