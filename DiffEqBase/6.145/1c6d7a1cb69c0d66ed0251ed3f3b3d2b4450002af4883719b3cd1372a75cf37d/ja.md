```julia
solve(prob::NonlinearProblem, alg::Union{AbstractNonlinearAlgorithm,Nothing}; kwargs...)
```

## 引数

唯一の位置引数は `alg` で、これはオプションです。デフォルトでは `alg = nothing` です。`alg = nothing` の場合、`solve` は NonlinearSolve.jl の自動アルゴリズム選択にディスパッチします（`using NonlinearSolve` が行われている場合、そうでなければ `MethodError` でエラーになります）。

## キーワード引数

NonlinearSolve.jl の宇宙には、`solve` 関数に利用可能な一般的な引数の大きなセットがあります。これらの引数は、任意の問題タイプの `solve` に適用され、特定の実装の制限によってのみ制限されます。

デフォルトの多くは、アルゴリズムまたはアルゴリズムが派生するパッケージに依存します。すべてのインターフェースがすべてのアルゴリズムによって提供されるわけではありません。特定のアルゴリズム/パッケージのデフォルトおよび利用可能なオプションに関する詳細情報については、特定の問題のソルバーのマニュアルページを参照してください。

#### エラー制御

  * `abstol`: 絶対許容誤差。
  * `reltol`: 相対許容誤差。

### その他

  * `maxiters`: 停止する前の最大反復回数。デフォルトは 1e5 です。
  * `verbose`: ソルバーが早期に終了したときに警告が表示されるかどうかを切り替えます。デフォルトは true です。

### 感度アルゴリズム (`sensealg`)

`sensealg` は、自動微分がどのように行われるかを選択するために使用されます。詳細については、SciMLSensitivity のドキュメントを参照してください: https://docs.sciml.ai/SciMLSensitivity/stable/
