```julia
NLSolveJL(;
          method=:trust_region,
          autodiff=:central,
          store_trace=false,
          extended_trace=false,
          linesearch=LineSearches.Static(),
          linsolve=(x, A, b) -> copyto!(x, A\b),
          factor = one(Float64),
          autoscale=true,
          m=10,
          beta=one(Float64),
          show_trace=false,
       )
```

### キーワード引数

  * `method`: 非線形システムを解くためのメソッドの選択。
  * `autodiff`: ヤコビアンを生成するためのメソッドの選択。デフォルトは `:central` または FiniteDiff.jlによる中央差分。その他の選択肢は `:forward`
  * `show_trace`: 最適化アルゴリズムの状態のトレースをSTDOUTに表示するべきか？ デフォルト: false.
  * `extended_trace`: 状態トレースに追加のアルゴリズム内部を追加するべきか？ デフォルト: false.
  * `linesearch`: ソルバーメソッド内で使用されるラインサーチメソッド。選択肢は [LineSearches.jl](https://github.com/JuliaNLSolvers/LineSearches.jl) のラインサーチタイプです。デフォルトは `LineSearches.Static()`。
  * `linsolve`: `Ax = b` を解く関数 `linsolve(x, A, b)`。デフォルトはJuliaの `\` を使用。
  * `factor``: 初期トラスト領域のサイズを決定します。このサイズは、非ゼロの場合は factor と`u0` のユークリッドノルムの積に設定され、そうでない場合は factor 自身に設定されます。デフォルト: 1.0.
  * `autoscale`: true の場合、変数は自動的に再スケーリングされます。スケーリングファクターはヤコビアン列のノルムです。デフォルト: true.
  * `m`: アンダーソン法における履歴の量。m=0に設定することで素朴な「ピカール」スタイルの反復が達成できますが、リプシッツ定数が1に近い収束に対しては推奨されません。ただし、収束に失敗した場合は、下げることを検討できます。
  * `beta`: DIISまたはPulay混合としても知られ、このメソッドは固定点反復 xₙ₊₁ = xₙ + beta*f(xₙ) の加速に基づいており、デフォルトでは beta=1 です。
  * `store_trace``: 最適化アルゴリズムの状態のトレースを保存するべきか？ デフォルト: false.

### サブメソッドの選択

`NLSolveJL` におけるメソッドの選択肢:

  * `:anderson`: アンダーソン加速固定点反復
  * `:broyden`: ブロイデンの準ニュートン法
  * `:newton`: オプションのラインサーチを伴う古典的ニュートン法
  * `:trust_region`: トラスト領域ニュートン法（デフォルトの選択）

これらの引数に関する詳細は、[NLsolve.jl ドキュメント](https://github.com/JuliaNLSolvers/NLsolve.jl)を参照してください。
