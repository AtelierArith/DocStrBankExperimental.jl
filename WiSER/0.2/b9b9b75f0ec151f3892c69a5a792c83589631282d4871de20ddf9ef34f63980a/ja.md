```
fit!(m::WSVarLmmModel, 
solver=IpoptSolver(print_level=0, mehrotra_algorithm="yes", max_iter=100);
init=init_ls!(m), runs = 2)
```

`WSVarLmmModel`オブジェクトを加重NLS法を使用してフィットします。

# 位置引数

  * `m::WSVarLmmModel`: フィットするモデル。
  * `solver`: 使用する非線形プログラミングソルバー。一般的な選択肢には次のものがあります：  

      * `Ipopt.IpoptSolver(print_level=0, mehrotra_algorithm="yes", warm_start_init_point="yes", max_iter=100)`。
      * `Ipopt.IpoptSolver(print_level=0, watchdog_shortened_iter_trigger=3, max_iter=100)`。
      * `Ipopt.IpoptSolver(print_level=0, max_iter=100)`。
      * `KNITRO.KnitroSolver(outlev=3)`。（Knitroは商用ソフトウェアです）
      * `NLopt.NLoptSolver(algorithm=:LD_MMA, maxeval=4000)`。
      * `NLopt.NLoptSolver(algorithm=:LD_LBFGS, maxeval=4000)`。

# キーワード引数

  * `init`: 初期化戦略。`fit!`は`m.τ`と`m.Lγ`を使用して重み行列`Vi`を設定し、加重NLSを解いて`m.β`、`m.τ`、および`m.Lγ`の推定値を取得します。`init`の選択肢には次のものがあります：  

      * `init_ls!(m)`（デフォルト）：最小二乗解析解によって初期化します。
      * `init_mom!(m)`：非加重NLS（MoM）によって初期化します。
      * `m`：ユーザーが提供した`m.τ`と`m.Lγ`の値から初期化します。
  * `runs::Integer`: 加重NLSの実行回数；デフォルトは2です。各実行は最新の`m.τ`と`m.Lγ`を使用して重み行列`Vi`を更新し、新しい加重NLSを解きます。
  * `parallel::Bool`: マルチスレッドを使用するかどうか。デフォルトは`false`です。
  * `verbose::Bool`: 詳細表示をするかどうか。デフォルトは`true`です。
