```
solve(system; kwargs...)
```

[`VoronoiFVM.System`](@ref) の組み込み解法メソッドです。

キーワード引数:

  * すべてのソルバーに共通

      * `inival` (デフォルト: 0) : [`unknowns`](@ref) を介して作成された配列または初期値を与える数値。
      * `control` (デフォルト: nothing): [`SolverControl`](@ref) のインスタンスを渡す
      * [`SolverControl`](@ref) のすべての要素をキーワード引数として使用できます。最終的に `control` を介して与えられた値を上書きします。
      * `params`: パラメータ（パラメータ処理は実験的であり、変更される可能性があります）
  * **定常ソルバー**: `times`、`embed`、`tstep` のいずれもキーワード引数として与えられない場合に呼び出されます。

      * `time` (デフォルト: `0.0`): 時間値を設定します。

    [`DenseSolutionArray`](@ref) または [`SparseSolutionArray`](@ref) を返します。
  * **埋め込み（ホモトピー）ソルバー**: `embed` キーワード引数が与えられた場合に呼び出されます。ホモトピー埋め込み + 減衰ニュートン法を使用して定常問題を解決するか、パラメータ依存の問題の系列を解決します。パラメータステップ制御はソルバー制御データに従って行われます。キーワード引数とデフォルト値は次のとおりです。

      * `embed` (デフォルト: `nothing` ): 正確に到達すべきパラメータ値のベクトル

    さらに、暗黙のオイラーソルバーのすべてのキーワード引数（`times` を除く）が処理されます。保存された解を含む過渡解オブジェクト `sol` を返します。詳細は [`TransientSolution`](@ref) を参照してください。
  * **暗黙のオイラー過渡ソルバー**: `times` キーワード引数が与えられた場合に呼び出されます。暗黙のオイラー法 + 減衰ニュートン法を使用して時間依存の問題を解決します。時間ステップ制御はソルバー制御データに従って行われます。キーワード引数とデフォルト値は次のとおりです。

      * `times` (デフォルト: `nothing` ): 正確に到達すべき時間値のベクトル
      * `pre` (デフォルト: `(sol,t)->nothing` ): 各時間ステップの前に呼び出されるコールバック
      * `post`  (デフォルト:  `(sol,oldsol, t, Δt)->nothing` ): 各時間ステップの後に呼び出されるコールバック
      * `sample` (デフォルト:  `(sol,t)->nothing` ): `times[2:end]` のすべての時間の時間ステップ後に呼び出されるコールバック。
      * `delta` (デフォルト:  `(system, u,v,t, Δt)->norm(sys,u-v,Inf)` ): 時間ステップサイズ `Δu` を制御するために使用される値

    `control.handle_error` が true の場合、時間ステップ解がエラーをスローすると、ステップサイズが下げられ、より小さな時間値でステップ解が再度呼び出されます。`control.Δt<control.Δt_min` の場合、解はエラーで中止されます。保存された解を含む過渡解オブジェクト `sol` を返します。詳細は [`TransientSolution`](@ref) を参照してください。
  * **暗黙のオイラー時間ステップソルバー**。 `tstep` キーワード引数が与えられた場合に呼び出されます。暗黙のオイラー法の1つの時間ステップを解決します。

      * `time` (デフォルト: `0`): 時間値を設定します。
      * `tstep`: 時間ステップ

    [`DenseSolutionArray`](@ref) または [`SparseSolutionArray`](@ref) を返します。
