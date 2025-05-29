```
(X, stats) = block_gmres(A, b::AbstractMatrix{FC};
                         memory::Int=5, M=I, N=I, ldiv::Bool=false,
                         restart::Bool=false, reorthogonalization::Bool=false,
                         atol::T=√eps(T), rtol::T=√eps(T), itmax::Int=0,
                         timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                         callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

```
(X, stats) = block_gmres(A, B, X0::AbstractMatrix; kwargs...)
```

Block-GMRES は初期推定値 `X0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

サイズ n の線形システム AX = B を p の右辺を使って block-GMRES で解きます。

#### インターフェース

ブロック Krylov メソッド間で簡単に切り替えるには、`method = :block_gmres` を使って汎用インターフェース [`krylov_solve`](@ref) を使用します。

解の間でメモリを再利用するインプレースバリアントについては、[`block_gmres!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `n` の行列をモデル化する線形演算子;
  * `B`: サイズ `n × p` の行列。

#### オプション引数

  * `X0`: サイズ `n × p` の行列で、解 `X` の初期推定値を表します。

#### キーワード引数

  * `memory`: `restart = true` の場合、再起動されたバージョン block-GMRES(k) が `k = memory` で使用されます。`restart = false` の場合、パラメータ `memory` は動的メモリ割り当てを制限するための反復回数のヒントとして使用されます。反復回数が `memory` を超えると追加のストレージが割り当てられます;
  * `M`: 左前処理に使用されるサイズ `n` の非特異行列をモデル化する線形演算子;
  * `N`: 右前処理に使用されるサイズ `n` の非特異行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `restart`: `memory` 回の反復後にメソッドを再起動します;
  * `reorthogonalization`: 新しいブロック-Krylov 基底の行列をすべての以前の行列に対して再直交化します;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `2 * div(n,p)` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムなどの実行に関する追加の統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、ブロック-Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力が記録されるストリーム。

#### 出力引数

  * `X`: サイズ `n × p` の密行列;
  * `stats`: [`SimpleStats`](@ref) 構造体に収集された実行中の統計。
