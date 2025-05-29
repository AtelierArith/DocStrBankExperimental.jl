```
Base.@kwdef struct StochasticEM<:AbstractEM
    rng::AbstractRNG = Random.GLOBAL_RNG
end
```

確率的EMアルゴリズムは、1985年にG. CeleuxとJ. Dieboltによって導入されました[*The SEM Algorithm: A probabilistic teacher algorithm derived from the EM algorithm for the mixture problem*](https://cir.nii.ac.jp/crid/1574231874553755008)。

デフォルトの乱数シードは`Random.GLOBAL_RNG`ですが、`StochasticEM(seed)`を介して変更することができます。
