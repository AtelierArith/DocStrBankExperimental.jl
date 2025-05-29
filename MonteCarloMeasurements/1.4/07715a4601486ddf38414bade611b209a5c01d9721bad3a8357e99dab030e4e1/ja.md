```
p = outer_product([rng::AbstractRNG,] dists::Vector{<:Distribution}, N=100_000)
```

各次元が `dists` の対応する単変量分布に従ってサンプリングされる多変量系統サンプルを作成します。`p::Vector{Particles}` を返し、各Particlesの長さはおおよそ `N` に等しくなります。粒子は、長さが N の d:th ルートで与えられるベクトルを系統的にサンプリングした `d` の外積を形成します。ここで `d` は `dists` の長さです。すべての粒子は独立であり、周辺分布は `dists` によって与えられます。

`MonteCarloMeasurements.⊗` も参照してください。
