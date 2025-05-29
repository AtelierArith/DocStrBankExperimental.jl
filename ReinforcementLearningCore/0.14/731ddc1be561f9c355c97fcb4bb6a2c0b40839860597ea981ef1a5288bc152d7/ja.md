```
EpsilonGreedyExplorer{T}(;kwargs...)
EpsilonGreedyExplorer(ϵ) -> EpsilonGreedyExplorer{:linear}(; ϵ_stable = ϵ)
```

> イプシロン・グリーディ戦略: 最良のレバーは試行の割合 `1 - epsilon` に対して選択され、レバーはイプシロンの割合でランダムに選択されます。 [Multi-armed_bandit](https://en.wikipedia.org/wiki/Multi-armed_bandit)


ここでは2種類のイプシロン減少戦略が実装されています（`linear` と `exp`）。

> イプシロン減少戦略: イプシロン・グリーディ戦略に似ていますが、実験が進むにつれてイプシロンの値が減少し、最初は非常に探索的な行動を取り、最後は非常に利用的な行動を取ります。 - [Multi-armed_bandit](https://en.wikipedia.org/wiki/Multi-armed_bandit)


# キーワード

  * `T::Symbol`: ウォームアップステップでイプシロンを計算する方法を定義します。サポートされている値は `linear` と `exp` です。
  * `step::Int = 1`: 現在のステップを記録します。
  * `ϵ_init::Float64 = 1.0`: 初期イプシロン。
  * `warmup_steps::Int=0`: `ϵ_init` を使用するステップ数。
  * `decay_steps::Int=0`: イプシロンが `ϵ_init` から `ϵ_stable` に減少するためのステップ数。
  * `ϵ_stable::Float64`: `warmup_steps + decay_steps` の後のイプシロン。
  * `is_break_tie=false`: `true` に設定すると、同じ最大値のアクションをランダムに選択します。
  * `rng=Random.default_rng()`: 内部RNGを設定します。

# 例

```julia
s_lin = EpsilonGreedyExplorer(kind=:linear, ϵ_init=0.9, ϵ_stable=0.1, warmup_steps=100, decay_steps=100)
plot([RLCore.get_ϵ(s_lin, i) for i in 1:500], label="linear epsilon")
s_exp = EpsilonGreedyExplorer(kind=:exp, ϵ_init=0.9, ϵ_stable=0.1, warmup_steps=100, decay_steps=100)
plot!([RLCore.get_ϵ(s_exp, i) for i in 1:500], label="exp epsilon")
```

![](https://github.com/JuliaReinforcementLearning/ReinforcementLearning.jl/raw/main/docs/src/assets/epsilon_greedy_selector.png)
