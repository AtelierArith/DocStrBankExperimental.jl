```
(x, stats) = minares(A, b::AbstractVector{FC};
                     M=I, ldiv::Bool=false,
                     λ::T = zero(T), atol::T=√eps(T),
                     rtol::T=√eps(T), Artol::T = √eps(T),
                     itmax::Int=0, timemax::Float64=Inf,
                     verbose::Int=0, history::Bool=false,
                     callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

```
(x, stats) = minares(A, b, x0::AbstractVector; kwargs...)
```

MINARES は初期推定値 `x0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

MINARES はサイズ n のエルミート線形システム Ax = b を解きます。MINARES は M = Iₙ の場合に ‖Arₖ‖₂ を最小化し、それ以外の場合は ‖AMrₖ‖*M を最小化します。各イテレーションで計算される推定値は ‖Mrₖ‖₂ と ‖AMrₖ‖*M です。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :minares` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用してください。

メモリを再利用するインプレースバリアントについては、[`minares!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `n` のエルミート正定値行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定値を表す長さ `n` のベクトル。

#### キーワード引数

  * `M`: 中心化前処理に使用されるサイズ `n` のエルミート正定値行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義;
  * `λ`: 正則化パラメータ;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `Artol`: Aᴴ-残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大イテレーション数。`itmax=0` の場合、デフォルトのイテレーション数は `2n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` イテレーションごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、それ以外の場合は `false` を返します;
  * `iostream`: 出力がログされるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体で実行中に収集された統計。

#### 参考文献

  * A. Montoison, D. Orban and M. A. Saunders, [*MinAres: An Iterative Solver for Symmetric Linear Systems*](https://doi.org/10.1137/23M1605454), SIAM Journal on Matrix Analysis and Applications, 46(1), pp. 509–529, 2025.
