```
    CalibrationProblem(times, volumes, model; learning_rate=0.0001, options...)
```

測定された `volumes` と対応する `times` に基づいて、腫瘍成長 `model` のパラメータを最適化する問題を指定します。

可能な `model` のリストについては、[`TumorGrowth`](@ref) を参照してください。

デフォルトの最適化は、二乗和損失を使用したAdam勾配降下法です。問題に対して `solve!` を呼び出して最適化を実行します。以下の例に示すように、早期停止を含む高度なオプションについては「拡張ヘルプ」を参照してください。

パラメータの初期値はデフォルトで推測されます。

凍結されていない限り（以下の「拡張ヘルプ」を参照）、キャリブレーションプロセスは一般的に `volumes[1]` とは異なる初期条件 `v0` を学習します。

# 簡単な解法

```julia
using TumorGrowth

times = [0.1, 6.0, 16.0, 24.0, 32.0, 39.0]
volumes = [0.00023, 8.4e-5, 6.1e-5, 4.3e-5, 4.3e-5, 4.3e-5]
problem = CalibrationProblem(times, volumes, gompertz; learning_rate=0.01)
solve!(problem, 30)    # 30回の勾配降下更新を適用
julia> loss(problem)   # 二乗和損失
1.7341026729860452e-9

p = solution(problem)
julia> pretty(p)
"v0=0.0002261  v∞=2.792e-5  ω=0.05731"


extended_times = vcat(times, [42.0, 46.0])
julia> gompertz(extended_times, p)[[7, 8]]
2-element Vector{Float64}:
 3.374100207406809e-5
 3.245628908921241e-5
```

# 拡張ヘルプ

# イテーション制御による解法

上記の例を続けて、`solve!(problem, n)` の反復回数 `n` を、IterationControl.jl の任意の制御に置き換えることができます：

```julia
using IterationControl
solve!(
  problem,
  Step(1),            # 1回ごとに制御を適用...
  WithLossDo(),       # 損失を表示
  Callback(problem -> print(pretty(solution(problem)))), # パラメータを表示
  InvalidValue(),     # ±Inf/NaN損失で停止
  NumberSinceBest(5), # 最低損失が5ステップ前だった場合に停止
  TimeLimit(1/60),    # 1分後に停止
  NumberLimit(400),   # 400ステップ後に停止
)
p = solution(problem)
julia> loss(problem)
7.609310030658547e-10
```

すべてのオプションについては、[IterationControl.jl](https://github.com/JuliaAI/IterationControl.jl) を参照してください。

!!! note
    上記のような制御された反復は、`optimiser=LevenbergMarquardt()` または `optimiser=Dogleg()` を指定した場合には推奨されません。なぜなら、これらの最適化手法の内部状態は毎回 `Step` でリセットされるからです。自動停止を設定するには、`solve!(problem, 0)` を使用してください。


# 結果の視覚化

```julia
using Plots
scatter(times, volumes, xlab="time", ylab="volume", label="train")
plot!(problem, label="prediction")
```

# キーワードオプション

  * `p0=guess_parameters(times, volumes, model)`: モデルパラメータの初期値。
  * `lower`: モデルパラメータ `p` の成分に対する下限を示す名前付きタプル。たとえば、`lower=(; v0=0.1)` の場合、これは制約 `p.v0 < 0.1` を導入します。モデル固有のデフォルト値は [`TumorGrowth.lower_default(model)`](@ref) です。
  * `upper`: モデルパラメータ `p` の成分に対する上限を示す名前付きタプル。たとえば、`upper=(; v0=100)` の場合、これは制約 `p.v0 < 100` を導入します。モデル固有のデフォルト値は [`TumorGrowth.upper_default(model)`](@ref) です。
  * `frozen`: 指定された値で凍結されるパラメータを示す名前付きタプル、たとえば `(; v0=nothing, λ=1/2)`。`nothing` の値は初期値で凍結することを意味します。モデル固有のデフォルト値は [`TumorGrowth.frozen_default(model)`](@ref) です。
  * `learning_rate > 0`: Adam勾配降下法最適化のための学習率。`optimiser` が明示的に指定されている場合は無視されます。
  * `optimiser`: 最適化アルゴリズムで、次の2種類のいずれかになります：

      * 勾配降下法の最適化手法：これはOptimisers.jlからのものであるか、同じAPIを実装している必要があります。
      * ガウス-ニュートン最適化手法：`LevenbergMarquardt()`、`Dogleg()`、LeastSquaresOptim.jlによって提供されます（ただし、`TumorGrowth`によって再エクスポートされています）。

    モデル固有のデフォルト値は [`TumorGrowth.optimiser_default(model)`](@ref) ですが、`learning_rate` が指定されている場合は `Optimisers.Adam(learning_rate)` になります。
  * `scale`: `p = scale(q)` が最適化されるモデルパラメータの同じオーダーの値を持つ性質を持つスケーリング関数。`q` がすべての値が1に等しいモデルパラメータ `p` と同じ形を持つ場合、スケーリングは `p` の成分が同じ速度で収束するのに役立ちます。ガウス-ニュートン最適化手法では無視されます。モデル固有のデフォルトは [`TumorGrowth.scale_default(model)`](@ref) です。
  * `radius > 0`: 初期信頼領域半径。これは `optimiser` がガウス-ニュートン最適化手法でない限り無視されます。モデル固有のデフォルトは [`TumorGrowth.radius_default(model, optmiser)`](@ref) で、通常 `LevenbergMarquardt()` では `10.0`、`Dogleg` では `1.0` です。
  * `half_life=Inf`: 二乗和損失を重み付きバージョンに置き換えるために実数の正の数に設定します。重みは指定された `half_life` で逆時間に減衰します。ガウス-ニュートン最適化手法では無視されます。
  * `penalty ≥ 0`: 正の値が大きいほど、損失ペナルティは `v0` と `v∞` の大きな違いを対数スケールで抑制します。これは、ODEが原点で特異点を持つモデルにおいて、`v0` と `v∞` が境界を超えないようにするのに役立ちます。モデルは `v0` と `v∞` をパラメータとして含む必要があります。ガウス-ニュートン最適化手法では無視されます。モデル固有のデフォルト値は [`TumorGrowth.penalty_default(model)`](@ref) です。
  * `ode_options...`: DifferentialEquations.jl のODEソルバー `DifferentialEquations.solve` に対するオプションのキーワード引数。解析解を使用するモデルには関連しません（[`TumorGrowth`](@ref) の表を参照）。
