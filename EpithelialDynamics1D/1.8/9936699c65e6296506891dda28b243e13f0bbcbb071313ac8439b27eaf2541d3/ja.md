```
CellProblem{F,DF,DP,G,GP}
```

セルシミュレーション問題を表すための構造体。

# フィールド

  * `force_law::F`: 力の法則、例: `(δ, p) -> p.k * (p.s - δ)`。
  * `force_law_parameters::Fp`: 力の法則のパラメータ。
  * `proliferation_law::G = (δ, p) -> zero(δ)`: 増殖の法則、例: `(δ, p) -> p.β`。
  * `proliferation_law_parameters::Gp = nothing`: 増殖の法則のパラメータ。
  * `proliferation_period::Float64 = 1e-2`: 増殖イベントを試みる頻度。
  * `initial_time::Float64 = 0.0`: 初期時間。
  * `final_time::Float64`: 最終時間。
  * `fix_left::Bool = true`: 左端点を固定するかどうか。
  * `fix_right::Bool = true`: 右端点を固定するかどうか。
  * `damping_constant::Float64`: 減衰定数。
  * `initial_condition::Vector{Float64}`: 初期のセルの位置。ソートされている必要があります。

# 解法

`CellProblem`は、DifferentialEquations.jlの問題を解くように解くことができます。例えば、

```
solve(prob, Tsit5(), saveat = 0.1)
```

`solve`に提供する他のキーワード引数は次のとおりです：

  * `proliferation::Bool = false`: 増殖を含めるかどうか。
  * `rng::AbstractRNG = Random.default_rng()`: 増殖に使用する乱数生成器。
  * `sort::Bool = false`: 各ステップ後にセルをソートするかどうか。これは、数値誤差や`F(q) = k/q^(n+1)`, `n ≥ 0`のような力の法則によってセルがソートされなくなるのを防ぐのに役立ちます。

増殖問題には、`EnsembleProblem`が役立つ場合があります - ドキュメントを参照してください。
