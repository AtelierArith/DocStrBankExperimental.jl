get_status(nlp, kwargs...)

キーワード引数の情報に基づいてソルバーの出力を返します。完全なリストについては `show_statuses()` を使用してください。

キーワード引数には以下が含まれる場合があります：

  * `elapsed_time::Float64 = 0.0`: 現在の経過時間（デフォルト: `0.0`）;
  * `iter::Integer = 0`: 現在の反復回数（デフォルト: `0`）;
  * `optimal::Bool = false`: 問題が最適解に達した場合は `true`（デフォルト: `false`）;
  * `small_residual::Bool = false`: 非線形最小二乗問題が小さな残差で解に達した場合は `true`（デフォルト: `false`）;
  * `infeasible::Bool = false`: 問題が実行不可能な場合は `true`（デフォルト: `false`）;
  * `parameter_too_large::Bool = false`: パラメータが大きすぎる場合は `true`（デフォルト: `false`）;
  * `unbounded::Bool = false`: 問題が無限大の場合は `true`（デフォルト: `false`）;
  * `stalled::Bool = false`: アルゴリズムが停滞している場合は `true`（デフォルト: `false`）;
  * `max_eval::Integer`: `eval_fun` によって定義された評価の最大数の制限（デフォルト: `typemax(Int)`）;
  * `max_time::Float64 = Inf`: 時間の制限（デフォルト: `Inf`）;
  * `max_iter::Integer`: 反復回数の制限（デフォルト: `typemax(Int)`）。
