```
sim(scenario::Scenario; 
  parameters::AbstractVector{<:Pair{Symbol,<:Real}}=Pair{Symbol, Float64}[],
  alg=DEFAULT_ALG, 
  reltol=DEFAULT_SIMULATION_RELTOL,
  abstol=DEFAULT_SIMULATION_ABSTOL,
  kwargs...)
```

単一の `Scenario` をシミュレートします。[`SimResult`](@ref) 型を返します。

例: `Scenario(model, (0., 200.); saveat = [0.0, 150.]) |> sim`

引数:

  * `scenario` : [`Scenario`](@ref) 型のシミュレーションシナリオ
  * `parameters` : `Model` と `Scenario` のパラメータを上書きするパラメータ。デフォルトは空のベクターです。
  * `alg` : ODE ソルバー。詳細については SciML ドキュメントを参照してください。デフォルトは AutoTsit5(Rosenbrock23()) です。
  * `reltol` : 相対許容誤差。デフォルトは 1e-3 です。
  * `abstol` : 絶対許容誤差。デフォルトは 1e-6 です。
  * `kwargs...` : SciMLBase.solve によってサポートされる他のソルバー関連の引数。詳細については SciML ドキュメントを参照してください。
