```
(X, stats) = block_minres(A, b::AbstractMatrix{FC};
                          M=I, ldiv::Bool=false,
                          atol::T=√eps(T), rtol::T=√eps(T), itmax::Int=0,
                          timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                          callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

```
(X, stats) = block_minres(A, B, X0::AbstractMatrix; kwargs...)
```

Block-MINRES は初期推定値 `X0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

サイズ n の Hermitian 線形システム AX = B を p 個の右辺を用いて block-MINRES で解きます。

#### インターフェース

ブロック Krylov メソッド間で簡単に切り替えるには、`method = :block_minres` を使用して一般的なインターフェース [`krylov_solve`](@ref) を利用してください。

解の間にメモリを再利用するインプレースバリアントについては、[`block_minres!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `n` の Hermitian 行列をモデル化する線形演算子;
  * `B`: サイズ `n × p` の行列。

#### オプション引数

  * `X0`: サイズ `n × p` の行列で、解 `X` の初期推定値を表します。

#### キーワード引数

  * `M`: 中心化前処理に使用されるサイズ `n` の Hermitian 正定値行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `2 * div(n,p)` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムなどの実行に関する追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、ブロック-Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力がログされるストリーム。

#### 出力引数

  * `X`: サイズ `n × p` の密行列;
  * `stats`: [`SimpleStats`](@ref) 構造体に収集された実行統計。
