```
ArmijoLinesearch <: Linesearch
```

最後の実行状態文字列と最後のステップサイズを含むArmijoラインサーチを表すファンクタ。

# フィールド

  * `initial_stepsize`:              (`1.0`) 初期ステップサイズ
  * `retraction_method`:             (`default_retraction_method(M)`) 使用するリトラクション
  * `contraction_factor`:            (`0.95`) ラインサーチの縮小のための指数
  * `sufficient_decrease`:           (`0.1`) Armijoのルール内の利得
  * `last_stepsize`:                 (`initialstepsize`) 検索を開始するための最後のステップサイズ
  * `initial_guess`:                 (`(p,s,i,l) -> l`)  [`AbstractManoptProblem`](@ref) `p`、[`AbstractManoptSolverState`](@ref) `s`、現在の反復 `i`、および最後のステップサイズ `l` に基づいて初期推測を返します。デフォルトでは、最後に得られたステップサイズを使用します。
  * `additional_decrease_condition`: (`(M,p) -> true`) 新しい点が追加で満たす必要がある条件を指定します。デフォルトではすべての点を受け入れます。
  * `additional_increase_condition`: (`(M,p) -> true`) 有効な増加を確認することに加えて満たす必要がある条件を指定します。デフォルトではすべての点を受け入れます。

内部使用のために

  * `candidate_point`:           (`allocate_result(M, rand)`) 中間結果を格納するため

さらに、以下のフィールドは安全装置として機能します

  * `stop_when_stepsize_less`:    (`0.0`) 停止する最小ステップサイズ（その前の最後のものが取られます）
  * `stop_when_stepsize_exceeds`: ([`max_stepsize`](@ref)`(M, p)`) 停止する最大ステップサイズ。
  * `stop_increasing_at_step`:    (`100`) ステップサイズを増加させる最後のステップ（フェーズ1）、
  * `stop_decreasing_at_step`:    (`1000`) ステップサイズを減少させる最後のステップサイズ（フェーズ2）、

これらが発生したときに `@info` を表示するには、 `debug=` に `:Messages` を渡します。

# コンストラクタ

```
ArmijoLinesearch(M=DefaultManifold())
```

フィールドのキーワード引数とリトラクションが `M` のデフォルトリトラクションに設定されます。

コンストラクタはArmijoラインサーチを実行するファンクタを返します。ここで、

```
(a::ArmijoLinesearch)(amp::AbstractManoptProblem, ams::AbstractManoptSolverState, i)
```

は [`AbstractManoptProblem`](@ref) `amp`、[`AbstractManoptSolverState`](@ref) `ams`、およびキーワードを持つ現在の反復 `i` です。

## キーワード引数

  * `candidate_point`: (`allocate_result(M, rand)`) 候補点のためのメモリを渡す
  * `η`:               (`-get_gradient(mp, get_iterate(s));`) 使用する探索方向、

デフォルトでは最急降下方向です。
