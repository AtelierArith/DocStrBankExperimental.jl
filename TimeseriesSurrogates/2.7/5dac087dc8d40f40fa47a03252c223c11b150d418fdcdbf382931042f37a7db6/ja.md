```
surrogenerator(x, method::Surrogate [, rng]) → sgen::SurrogateGenerator
```

要求に応じて `x` の代理を生成するジェネレーターを初期化します。これは、与えられた `method` に基づいています。ほとんどのメソッドでは、いくつかのものを初期化してすべての代理に再利用できるため、[`surrogate`](@ref) よりも効率的です。オプションで、ランダム数生成を制御し、生成された代理の再現性を確立する `rng::AbstractRNG` オブジェクトを提供できます。デフォルトでは `Random.default_rng()` が使用されます。

生成された代理は、共通のベクターコンテナをインプレースで上書きします。複数の代理を実際に保存する必要がある場合は、`copy` を使用してください。

代理を生成するには、引数なしで関数として `sgen` を呼び出します。例えば：

```julia
sgen = surrogenerator(x, method)
s = sgen()
```

Julia のジェネレーター構文を使用して、`sg` によって生成された代理に対してマッピングできます。例えば、`q` を差別的統計を返す関数とします。TimeseriesSurrogates.jl でいくつかの帰無仮説をテストするには、次のようにします。

```julia
using TimeseriesSurrogates
q, x # 入力
method = RandomFourier() # 一例のメソッド
sgen = surrogenerator(x, method)
siter = (sgen() for _ in 1:1000)
qx = q(x)
qs = map(q, siter)
# `qx` を分位数と比較
using Statistics: quantile
q01, q99 = quantile(qs, [0.01, 0.99])
q01 ≤ qx ≤ q99 # 偽の場合、仮説を棄却できます！
```
