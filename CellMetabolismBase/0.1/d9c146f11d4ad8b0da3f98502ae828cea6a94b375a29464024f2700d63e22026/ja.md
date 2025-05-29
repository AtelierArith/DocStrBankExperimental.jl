```
make_EnsembleProblem(metab_path, vect_init_cond, vect_params; tspan=(0.0, 1e8))
```

複数の初期条件とパラメータを持つ代謝経路シミュレーションのための`EnsembleProblem`を作成します。

# 引数

  * `metab_path::MetabolicPathway`: シミュレーションする代謝経路モデル。
  * `vect_init_cond::Vector{<:LArray}`: 各アンサンブルメンバーの初期条件のベクトル。
  * `vect_params::Vector{<:LArray}`: 各アンサンブルメンバーのパラメータのベクトル。
  * `tspan::Tuple{Float64,Float64}=(0.0, 1e8)`: シミュレーションの時間範囲。

# 戻り値

  * `EnsembleProblem`: DifferentialEquations.jlのアンサンブルソルバーを使用して解決できるアンサンブル問題。

# 注意事項

  * `vect_init_cond`と`vect_params`は同じ長さでなければなりません。
  * アンサンブル内の各要素は、提供されたベクトルから対応する初期条件とパラメータを使用します。
  * アンサンブル問題は、初期条件とパラメータベクトルの最初の要素を使用して作成された基本的なODE問題から構築されます。

# 例

```julia
using CellMetabolismBase
using DifferentialEquations

metab_path = MetabolicPathway(...)
init_cond = LArray(...)
params = LArray(...)
tspan = (0.0, 1e8)
ensemble_prob = make_EnsembleProblem(metab_path, [init_cond1, init_cond2], [params1, params2], tspan)
ensemble_sol = solve(ensemble_prob, RadauIIA9(), trajectories=2)
```
