```
MDP(ns, na; init = "random")
MDP(; ns = 10, na = 4, init = "random")
```

`init`が("random", "uniform", "deterministic")のいずれかであるMDPを返します。キーワード`init`は遷移確率を構築する方法を決定します（[`getprobvecrandom`](@ref)、[`getprobvecuniform`](@ref)、[`getprobvecdeterministic`](@ref)も参照してください）。
