```
sim(scenario_pairs::Vector{P}; 
  parameters::AbstractVector{<:Pair{Symbol, <:Real}}=Pair{Symbol, Float64}[],
  alg=DEFAULT_ALG, 
  reltol=DEFAULT_SIMULATION_RELTOL, 
  abstol=DEFAULT_SIMULATION_ABSTOL,
  parallel_type=EnsembleSerial(),
  kwargs...) where P<:Pair
```

複数のシナリオをシミュレートします。`Vector{Pair}`を返します。

例: `sim([:x => scn1, :y=>scn2, :z=>scn3])`

引数:

  * `scenario_pairs` : [`Scenario`](@ref)の名前とシナリオを含むペアのベクター
  * `parameters` : `Model`および`Scenario`のパラメータを上書きするパラメータ。デフォルトは空のベクターです。
  * `alg` : ODEソルバー。詳細についてはSciMLのドキュメントを参照してください。デフォルトはAutoTsit5(Rosenbrock23())です。
  * `reltol` : 相対許容誤差。デフォルトは1e-3です。
  * `abstol` : 絶対許容誤差。デフォルトは1e-6です。
  * `parallel_type` : 複数のシミュレーションの並列性のタイプ。デフォルトは並列性なしです。詳細についてはSciMLのドキュメントを参照してください。
  * `kwargs...` : SciMLBase.solveによってサポートされる他のソルバー関連の引数。詳細についてはSciMLのドキュメントを参照してください。
