```
stochastic_triple(X, p; backend=PrunedFIsBackend(), direction=nothing)
stochastic_triple(p; backend=PrunedFIsBackend(), direction=nothing)
```

[`Functors.jl`](https://fluxml.ai/Functors.jl/stable/) によってサポートされている任意の `p` について、スカラーや抽象配列など、`p` の各値に関して出力を微分し、`p` と同様の構造の出力を返します。特定の値には、対応する `p` の値を摂動させたときの `X` のストキャスティックトリプル出力が含まれます（すなわち、元の値 `x` を `x + ε` に置き換えます）。

`direction` が提供されている場合、特定の方向での `p` の摂動に関する `X` のストキャスティックトリプル出力のみを返します。`X` が提供されていない場合、恒等関数が使用されます。

`backend` キーワード引数は、ストキャスティックトリプルの第3成分で使用されるアルゴリズムを説明します。詳細については、[技術的詳細](devdocs.md)を参照してください。

# 例

```jldoctest
julia> using Distributions, Random, StochasticAD; Random.seed!(4321);

julia> stochastic_triple(rand ∘ Bernoulli, 0.5)
StochasticTriple of Int64:
0 + 0ε + (1 with probability 2.0ε)
```
