```
cvar_rbp(B::Vector{Float64}, α::Float64, loss_sampler::Function; maxiters::Int=10000)
```

リスク嗜好が `B` にあり、相対損失のサンプルベクトルを返す関数 `loss_sampler()` がある場合、CV@R-`alpha` リスクバジェットポートフォリオを構築するために資産の投資ウェイトを計算します。

アルゴリズムは `maxiters` 回の反復後、すなわち `maxiters` ベクトルの相対損失をサンプリングした後に停止します。

戻り値は w :: Vector{Float64} です。

アルゴリズムの詳細については、`sgd_Lagrangian` を参照してください。
