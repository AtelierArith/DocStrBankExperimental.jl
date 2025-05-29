```julia
# スレッドの数と剛性ODEソルバーアルゴリズムを指定します。
# `timestep`は各分割ステップの時間の長さです。
SimulatorStrangThreads(threads, stiffalg, timestep; stiff_kwargs...)
# デフォルトのスレッド数を使用します。
SimulatorStrangThreads(stiffalg, timestep; stiff_kwargs...)
```

剛性と仮定されるMTKシステムに対して[ストラング分割](https://en.wikipedia.org/wiki/Strang_splitting)を使用してシミュレーションを実行します。剛性ODEシステムの解は、指定されたスレッド数を使用してグリッドセル全体に並列化されます。

  * `threads`: 使用するスレッドの数
  * `stiffalg`: 使用する剛性ソルバーアルゴリズム（https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/を参照）
  * `timestep`: 各分割時間ステップの長さ
  * `stiff_kwargs`: 剛性ODEProblemコンストラクタおよびソルバーのキーワード引数。
  * `alg`: グリッド計算を実行するためのアルゴリズム。
