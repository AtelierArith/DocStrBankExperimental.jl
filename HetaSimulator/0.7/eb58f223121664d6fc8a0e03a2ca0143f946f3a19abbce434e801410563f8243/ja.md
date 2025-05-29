```
mc(scenario::Scenario,
  parameters_variation::Vector{<:Pair},
  num_iter::Int;
  verbose=false,
  alg=DEFAULT_ALG,
  reltol=DEFAULT_SIMULATION_RELTOL,
  abstol=DEFAULT_SIMULATION_ABSTOL,
  parallel_type=EnsembleSerial(),
  kwargs...
)
```

単一の `Scenario` でモンテカルロシミュレーションを実行します。 [`MCResult`](@ref) 型を返します。

例: `mc(scenario, [:k2=>Normal(1e-3,1e-4), :k3=>Uniform(1e-4,1e-2)], 1000)`

引数:

  * `scenario` : [`Scenario`](@ref) 型のシミュレーションシナリオ
  * `parameters_variation` : パラメータの変動設定
  * `num_iter` : モンテカルロイテレーションの回数
  * `verbose` : イテレーションの進行状況を表示します。デフォルトは `false`
  * `progress_bar` : 進行状況バーを表示します。デフォルトは `false`
  * `alg` : ODE ソルバー。詳細は SciML ドキュメントを参照してください。デフォルトは AutoTsit5(Rosenbrock23())
  * `reltol` : 相対許容誤差。デフォルトは 1e-3
  * `abstol` : 絶対許容誤差。デフォルトは 1e-6
  * `output_func` : 解から出力配列に保存されるものを決定する関数。デフォルトは解自体を保存
  * `reduction_func` : 各バッチのデータをどのように集約するかを決定する関数。デフォルトはバッチからのデータを追加すること
  * `parallel_type` : 並列設定。詳細は SciML ドキュメントを参照してください。デフォルトは並列処理なし: EnsembleSerial()
  * kwargs : SciMLBase.solve によってサポートされる他のソルバー関連の引数。詳細は SciML ドキュメントを参照してください
