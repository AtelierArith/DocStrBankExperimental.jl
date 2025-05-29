```
solve(f; options...)
solve(f, start_solutions; start_parameters, target_parameters, options...)
solve(f, start_solutions; start_subspace, target_subspace, options...)
solve(g, f, start_solutions; options...)
solve(homotopy, start_solutions; options...)
```

与えられた問題を解決します。単一の多項式系 `f` のみが与えられた場合、すべての（複素）孤立解が計算されます。パラメータに依存する系 `f` と開始およびターゲットパラメータが与えられた場合、パラメータホモトピーが実行されます。系 `g` と `f` の2つが与えられ、`g` の解がある場合、`g` が `f` に変形する際に解が追跡されます。同様に、$t=1$ での解を持つホモトピー `homotopy` に対して、$t=0$ での解が計算されます。例についてはドキュメントを参照してください。入力が*同次*多項式系である場合、射影空間のランダムアフィンチャート上の解が計算されます。

## 一般オプション

`solve` ルーチンは次のオプションを受け取ります：

  * `catch_interrupt = true`: これが `true` の場合、計算が中断されたときに計算が優雅に停止し、部分的な結果が返されます。
  * `compile = mixed`: `true` の場合、`System`（または `Homotopy`）が評価のために直線プログラム（[`CompiledSystem`](@ref) または [`CompiledHomotopy`](@ref)）にコンパイルされます。これにはコンパイルのオーバーヘッドが発生します。`false` の場合、生成されたプログラムは単に解釈されます（[`InterpretedSystem`](@ref) または [`InterpretedHomotopy`](@ref)）。これはコンパイルされたバージョンよりも遅いですが、コンパイルのオーバーヘッドを導入しません。
  * `endgame_options`: エンドゲームのためのオプションとパラメータ。[`EndgameOptions`](@ref) を参照してください。
  * `seed`: 計算中に使用されるランダムシード。シードは結果にも報告されます。特定のランダムシードに対して、結果は常に同一です。
  * `show_progress= true`: 進行状況バーを表示するかどうかを示します。
  * `stop_early_cb`: ここでは、`PathResult` `r` を入力として受け取り、`Bool` を返す関数（または任意の呼び出し可能な構造体）を提供することができます。`stop_early_cb(r)` が `true` の場合、これ以上のパスは追跡されず、計算が終了します。これは成功したパスに対してのみ呼び出されます。これは、特定の多項式系の解を1つだけ計算したい場合に便利です。この場合、`stop_early_cb = _ -> true` で十分です。
  * `threading = true`: 計算のためにマルチスレッドを有効にします。使用可能なスレッドの数は環境変数 `JULIA_NUM_THREADS` によって制御されます。注意：一部のCPUは複数のスレッドを使用するとハングします。これを避けるために、REPL用に1つのインタラクティブスレッドと他のタスク用に `n` スレッドでJuliaを実行します（例：`julia -t 8,1` は `n=8` の場合）。
  * `tracker_options`: パストラッカーのためのオプションとパラメータ。[`TrackerOptions`](@ref) を参照してください。

## 入力に依存するオプション

単一の多項式系が与えられた場合：

  * `start_system`: 可能な値は `:total_degree` と `:polyhedral` です。選択に応じてさらにオプションが可能です。[`total_degree`](@ref) と [`polyhedral`](@ref) も参照してください。

パラメータに依存する系 `f` と開始パラメータ（または開始部分空間）、開始解、および*複数の*ターゲットパラメータ（またはターゲット部分空間）が与えられた場合、次のオプションも利用可能です：

  * `flatten`: `transform_result` の出力をフラットにします。これは、`transform_result` が解のベクトルを返し、結果として単一の解のベクトルのみを望む場合に便利です（解のベクトルのベクトルの代わりに）。
  * `transform_parameters = identity`: パラメータ値 `p` を `target_parameters = ...` に渡す前に変換します。
  * `transform_result`: 2つの引数、`result` とパラメータ `p` を取る関数。デフォルトでは、これはタプル `(result, p)` を返します。

## 基本的な例

```julia-repl
julia> @var x y;

julia> F = System([x^2+y^2+1, 2x+3y-1])
System of length 2
 2 variables: x, y

 1 + x^2 + y^2
 -1 + 2*x + 3*y

julia> solve(F)
Result with 2 solutions
=======================
• 2 non-singular solutions (0 real)
• 0 singular solutions (0 real)
• 2 paths tracked
• random seed: 0x75a6a462
• start_system: :polyhedral
```
