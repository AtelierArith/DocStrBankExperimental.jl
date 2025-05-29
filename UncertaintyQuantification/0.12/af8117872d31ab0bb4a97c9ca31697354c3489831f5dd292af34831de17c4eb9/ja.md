```
SubSetInfinityAdaptive(n::Integer, target::Float64, levels::Integer, Na::Integer, λ::Real, s::Real)
```

実装: Papaioannou, Iason, et al. "MCMC algorithms for subset simulation." Probabilistic Engineering Mechanics 41 (2015): 89-103

`n` はレベルごとのサンプル数、`target` は各レベルでの故障の目標確率、`levels` は最大レベル数、`λ` (λ = 1 推奨) は初期スケーリングパラメータ、`Na` は `λ` が更新される前に実行されるシミュレーションの数を定義します。Na は n * target の倍数でなければなりません: `mod(ceil(n * target), Na) == 0)`。提案分布の初期分散は `s` です。

このアルゴリズムの背後にあるアイデアは、中間レベルごとに `s` の相関パラメータを適応的に選択することであり、サブセット Na のチェーンをシミュレートし（無作為に置換なしで選択する必要があります）、最適な受け入れ率 αstar = 0.44 に向けて受け入れ率を修正します。

# コンストラクタ

  * `SubSetInfinityAdaptive(n::Integer, target::Float64, levels::Integer, Na::Integer)`   (デフォルト: λ = s = 1)
  * `SubSetInfinityAdaptive(n::Integer, target::Float64, levels::Integer, Na::Integer, λ::Real)` (λ = s)
  * `SubSetInfinityAdaptive(n::Integer, target::Float64, levels::Integer, Na::Integer, λ::Real, s::Real)`

# 注意

以下のコンストラクタは同じ数のサンプルを実行しますが、SubSetInfinityAdaptive は各チェーンの後に `s` を更新します:

  * `SubSetInfinityAdaptive(400, 0.1, 10, 40)`
  * `SubSetInfinity(400, 0.1, 10, 0.5)`

# 例

```jldoctest
julia> SubSetInfinityAdaptive(200, 0.1, 10, 2)
SubSetInfinityAdaptive(200, 0.1, 10, 2, 1, 1)
```

# 参考文献

[papaioannou2015mcmc](@cite)

[chan2022adaptive](@cite)
