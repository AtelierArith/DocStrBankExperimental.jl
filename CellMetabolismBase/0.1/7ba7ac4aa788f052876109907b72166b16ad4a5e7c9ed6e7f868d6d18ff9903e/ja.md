```
make_ODEProblem(metabolic_pathway, init_cond, tspan, params)
```

代謝経路をシミュレーションするためのODEProblemを構築します。

# 引数

  * `metabolic_pathway::MetabolicPathway`: 基質、生成物、および関連する反応の詳細を含む代謝経路を定義する構造体。
  * `init_cond::LArray`: 代謝物の初期条件。
  * `tspan::Tuple{<:Number, <:Number}`: シミュレーションの開始時刻と終了時刻を指定するタプル。
  * `params::LArray`: 代謝反応で使用されるパラメータ（例：動力学定数）。

# 戻り値

代謝経路を支配する微分方程式をカプセル化した`ODEProblem`インスタンス。この問題は、SciMLBaseのODEソルバーを使用して解決できます。

# 詳細

返されるODEProblemは、`metabolicpathway_odes!`を使用して、`enzyme_rates`で定義された酵素動力学に基づいて代謝物濃度の時間的変化を計算します。正しいシミュレーションのために、`metabolic_pathway`、`init_cond`、および`params`が基質、生成物、およびパラメータの一致するエントリを持っていることを確認してください。

# 例

```julia
using CellMetabolismBase
using DifferentialEquations

metab_path = MetabolicPathway(...)
init_cond = LArray(...)
tspan = (0.0, 1e8)
params = LArray(...)
prob = make_ODEProblem(metab_path, init_cond, tspan, params)
sol = solve(prob, RadauIIA9(), abstol=1e-15, reltol=1e-8)
```
