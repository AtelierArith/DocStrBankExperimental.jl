```
initialize_state_draws(s0::Vector{Float64}, F_ϵ::Distribution, Φ::Function,
                       n_parts::Int; burn::Int = 10000, thin::Int = 5)
```

### 入力

  * `s0::Vector`: 状態を前方に反復するための初期推測/開始点。
  * `F_ϵ::Distribution`: ショック分布: ϵ ~ F_ϵ
  * `Φ::Function`: 状態遷移関数: s*t = Φ(s*t-1, ϵ_t)
  * `n_parts::Int`: 生成する粒子（ドロー）の数

### キーワード引数

  * `initialize::Bool`: 重みの初期化中に増分重みを解決しているかどうかを示すフラグ; デフォルトは `false`。
  * `burn::Int`: 実際にドローが収集される前に燃焼するドローの数。この仮定は、s_t が燃焼後に定常分布に達することに基づいています。
  * `thin::Int`: 直列相関を最小限に抑えるために薄くするドローの数

### 出力

  * `s_init`: 開始するための状態の初期ドローを含む行列（#の状態 x #の粒子）
