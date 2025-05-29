```
NLsolveJL(;
    method = :trust_region, autodiff = :central, linesearch = Static(),
    linsolve = (x, A, b) -> copyto!(x, A\b), factor = one(Float64), autoscale = true,
    m = 10, beta = one(Float64)
)
```

### キーワード引数

  * `method`: 非線形システムを解くためのメソッドの選択。
  * `autodiff`: ヤコビアンを生成するためのメソッドの選択。デフォルトは `:central` または FiniteDiff.jlによる中央差分です。他の選択肢は、非線形解法の他のソルバーに似た `:forward` または `ADTypes` です。
  * `linesearch`: ソルバーメソッド内で使用されるラインサーチメソッド。選択肢は [LineSearches.jl](https://github.com/JuliaNLSolvers/LineSearches.jl) からのラインサーチタイプです。
  * `linsolve`: `Ax = b` を解く関数 `linsolve(x, A, b)`。
  * `factor`: 初期トラスト領域のサイズを決定します。このサイズは、非ゼロの場合は factor と `u0` のユークリッドノルムの積に設定され、そうでない場合は factor 自体に設定されます。
  * `autoscale`: true の場合、変数は自動的に再スケーリングされます。スケーリングファクターはヤコビアン列のノルムです。
  * `m`: アンダーソン法における履歴の量。m=0に設定することで素朴な「ピカール」スタイルの反復が達成できますが、リプシッツ定数が1に近い収束に対しては推奨されません。ただし、収束に失敗した場合は、下げることを検討できます。
  * `beta`: DIISまたはPulay混合としても知られ、このメソッドは固定点反復 xₙ₊₁ = xₙ + beta*f(xₙ) の加速に基づいており、デフォルトでは beta = 1 です。

!!! 警告     [`LineSearch.jl`](https://github.com/SciML/LineSearch.jl) のラインサーチアルゴリズムは `NLsolveJL` ではサポートされていません。代わりに、[`LineSearches.jl`](https://github.com/JuliaNLSolvers/LineSearches.jl) のラインサーチアルゴリズムを使用してください。

### サブメソッドの選択

`NLsolveJL` のメソッドの選択肢：

  * `:anderson`: アンダーソン加速固定点反復
  * `:broyden`: ブロイデンの準ニュートン法
  * `:newton`: オプションのラインサーチを伴う古典的ニュートン法
  * `:trust_region`: トラスト領域ニュートン法（デフォルトの選択）

これらの引数に関する詳細は、[NLsolve.jl ドキュメント](https://github.com/JuliaNLSolvers/NLsolve.jl)を参照してください。

!!! 注     このアルゴリズムは `NLsolve.jl` がインストールされ、ロードされている場合にのみ利用可能です。
