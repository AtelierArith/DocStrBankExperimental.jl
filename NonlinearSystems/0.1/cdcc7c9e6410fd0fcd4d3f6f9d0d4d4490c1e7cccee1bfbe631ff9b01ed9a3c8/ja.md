```
HybridSolver(fdf::OnceDifferentiable, x, fx, J, P; kwargs...)
```

`HybridSolver`を構築して、[`Hybrid`](@ref)メソッドを使用してタイプ`P`の問題を解決します。このメソッドを直接呼び出すことはユーザーに期待されておらず、代わりに`init`または`solve`にキーワード引数を渡すべきです。詳細は[`Hybrid`](@ref)を参照してください。

# キーワード

  * `linsolver=default_linsolver(fdf, x0, P)`: 基本的な線形問題のためのソルバー。
  * `factor_init::Real=1.0`: 初期信頼領域半径をスケーリングするための係数。
  * `factor_up::Real=2.0`: 信頼領域半径を拡大するための係数。
  * `factor_down::Real=0.5`: 信頼領域半径を縮小するための係数。
  * `scaling::Bool=true`: 信頼領域のスケーリングを改善することを許可します。
  * `rank1update::Bool=true`: ヤコビ行列と因子分解のためにランク-1更新を使用することを許可します。
  * `thres_jac::Integer=2`: 信頼領域が指定された回数連続して縮小された場合にヤコビ行列を再計算します。非正の値を設定すると、各ステップの後にヤコビ行列が再計算されます。
  * `thres_nslow1::Integer=10`: 残差ノルムの減少が指定された回数の連続ステップで小さいままである場合、遅いソルバーの進行を通知します。
  * `thres_nslow2::Integer=5`: 指定された回数の連続ステップでヤコビ行列を再計算した後に信頼領域の拡大がない場合、遅いソルバーの進行を通知します。
  * `warn::Bool=true`: 遅いソルバーの進行に対して警告メッセージを印刷します。
