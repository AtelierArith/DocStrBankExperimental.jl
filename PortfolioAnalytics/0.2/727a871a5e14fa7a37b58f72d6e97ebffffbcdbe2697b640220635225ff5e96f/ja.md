```
portfolio_optimize(R::TSFrame, objective::String = "minumum variance"; target = Nothing, Rf::Number = 0)
```

与えられた `objective` と `target` リターンに対する `最適ポートフォリオの重み` を計算します。

# 引数:

  * `R::TSFrame`: 資産リターンの TSFrame オブジェクトの列
  * `objective::String = "minumum variance"`: ポートフォリオの目的で、ポートフォリオの標準偏差を最小化します。利用可能な目的; `"minumum variance"` と `"maximum sharpe"`
  * `target = Nothing`: 選択した目的のためのターゲットポートフォリオ平均リターン。効率的フロンティアを横断することを可能にします
  * `Rf::Number = 0`: リスクフリーレート、`maximum sharpe` と共に使用されます

# 例

```julia
julia> opt1 = portfolio_optimize(returns, "minumum variance")
julia> opt_weights = opt1.pweights
3-element Named Vector{Float64}
Optimal Weights  │
─────────────────┼───────
TSLA             │   -0.0
NFLX             │ 0.4438
MSFT             │ 0.5562


# 効率的フロンティアと意思決定空間のプロット
julia> opt1.plt
```

最小リターンターゲット4%での最小分散ポートフォリオの最適化

```julia
julia> opt2 = portfolio_optimize(returns, "minumum variance", target = 0.04)

# 選択した目的とターゲットリターンのための最適ポートフォリオの重み
julia> opt2.pweights
3-element Named Vector{Float64}
Optimal Weights  │
─────────────────┼───────
TSLA             │ 0.5142
NFLX             │    0.0
MSFT             │ 0.4858
```

最大シャープポートフォリオの最適化

```julia
julia> opt3 = portfolio_optimize(returns, "maximum sharpe")
julia> opt3.pweights
3-element Named Vector{Float64}
Optimal Weights  │
─────────────────┼─────
TSLA             │ -0.0
NFLX             │  0.0
MSFT             │  1.0

julia> opt3.plt
```

ターゲットリターンが少なくとも4%の最大シャープポートフォリオの最適化

```julia
julia> opt4 = portfolio_optimize(returns, "maximum sharpe", target = 0.04)
julia> opt4.pweights
3-element Named Vector{Float64}
Optimal Weights  │
─────────────────┼───────
TSLA             │ 0.5142
NFLX             │   -0.0
MSFT             │ 0.4858
```

# 出力:

Named Tuple

  * 1, `preturn` : ポートフォリオの平均リターン
  * 2, `prisk`: ポートフォリオの標準偏差
  * 3, `psharpe`: ポートフォリオのシャープレシオ
  * 4, `pweights`: 選択した `objective` と定義された `target` のための最適ポートフォリオの重み
  * 5, `plt`: `効率的フロンティア` と `意思決定空間` のプロット
  * 6, `pm`: 各解の `期待リターン` のリスト
  * 7, `po`: 各ポートフォリオの目的値のリスト。目的が `最小分散` の場合、各最適ポートフォリオの標準偏差。目的が `最大シャープ` に設定されている場合、各ポートフォリオのシャープレシオ。
  * 8, `pw`: 各解の `重み` のリスト
