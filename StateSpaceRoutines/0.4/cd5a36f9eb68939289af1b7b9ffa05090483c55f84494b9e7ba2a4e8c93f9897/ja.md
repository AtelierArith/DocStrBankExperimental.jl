```
tempered_particle_filter(data, Φ, Ψ, F_ϵ, F_u, s_init; verbose = :high,
    n_particles = 1000, fixed_sched = [], r_star = 2, findroot = bisection,
    xtol = 1e-3, resampling_method = :multionial, n_mh_steps = 1, c_init = 0.3,
    target_accept_rate = 0.4, n_presample_periods = 0, allout = true,
    parallel = false, verbose = :low,
    dynamic_measurement = false, poolmodel = false)
```

### 入力

  * `data::Matrix{S}`: `Ny` x `Nt` の履歴データの行列
  * `Φ::Function`: 状態遷移方程式: s*t = Φ(s*{t-1}, ϵ_t)
  * `Ψ::Function`: 測定方程式: y*t = Ψ(s*t) + u_t
  * `F_ϵ::Distribution`: ショック分布: ϵ*t ~ F*ϵ
  * `F_u::Distribution`: 測定誤差分布: u*t ~ F*u
  * `s_init::Matrix{S}`: `Ns` x `n_particles` の初期状態ベクトル s_0 の行列

ここで `S<:AbstractFloat` であり

  * `Ns` は状態の数
  * `Ny` は観測可能な数
  * `Nt` はデータ期間の数

### キーワード引数

  * `n_particles::Int`: 対数尤度を近似するために使用される粒子の数。より多くの粒子を使用すると、より正確な推定が得られますが、計算負荷が高くなります。

**修正:**

  * `fixed_sched::Vector{S}`: 固定の温度スケジュールを指定する (0,1] の単調増加値の配列。適応的に温度スケジュールを選択したい場合は `[]` に設定します（以下参照）。
  * `r_star::S`: φを適応的に選択するために使用される目標非効率比、すなわち Ineff(φ*n) := 1/M Σ*{j=1}^M (Wtil*t^{j,n}(φ*n))^2 = r_star
  * `findroot::Function`: 根を見つけるアルゴリズム、`bisection` または `fzero` のいずれか
  * `xtol::S`: x ブラケットサイズに関する根を見つける許容誤差

**選択:**

  * `resampling_method::Symbol`: `:multinomial` または `:systematic` のいずれか

**変異:**

  * `n_mh_steps::Int`: 各温度段階で行うメトロポリス・ヘイスティングスのステップ数
  * `c_init::S`: 提案共分散行列の初期スケーリング
  * `target_accept_rate::S`: メトロポリス・ヘイスティングスの受け入れ率の目標

**その他:**

  * `n_presample_periods::Int`: 対数尤度計算から省略する初期期間の数
  * `allout::Bool`: すべての出力を返すか、`sum(loglh)` のみを返すか
  * `parallel::Bool`: `DistributedArray` を使用するかどうか
  * `verbose::Symbol`: STDOUT に出力する量。`:none`、`:low`、または `:high` のいずれか

### 出力

  * `sum(loglh)::S`: 対数尤度 p(y*{1:T}|Φ,Ψ,F*ϵ,F_u) の近似
  * `loglh::Vector{S}`: 条件付き対数尤度 p(y*t|y*{1:t-1},Φ,Ψ,F*ϵ,F*u) のベクトル
  * `times::Vector{S}`: 各期間 t の実行時間のベクトル
