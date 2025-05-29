```julia
# 硬いODEソルバーアルゴリズムを指定します。
# `timestep`は各分割ステップの時間の長さです。
SimulatorStrangSerial(stiffalg, timestep; stiff_kwargs...)
```

[ストラング分割](https://en.wikipedia.org/wiki/Strang_splitting)を使用してシミュレーションを実行します。ここで、MTKシステムは硬いと仮定され、演算子は非硬いと仮定されます。解は直列で計算されます。

ODEProblemコンストラクタの追加のkwargs:

  * u0: 初期条件; "nothing"の場合、デフォルト値が使用されます。
  * p: パラメータ; "nothing"の場合、デフォルト値が使用されます。
  * `stiffalg`: 使用する硬いソルバーアルゴリズム（https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/を参照）
  * `timestep`: 各分割時間ステップの長さ
  * `stiff_kwargs`: 硬いODEProblemコンストラクタおよびソルバーのキーワード引数。
  * `alg`: グリッド計算を実行するためのアルゴリズム。

警告: この戦略を使用してパラメータを変更することはできません..
