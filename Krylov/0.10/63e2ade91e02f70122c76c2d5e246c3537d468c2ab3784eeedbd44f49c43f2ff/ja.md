```
(x, stats) = qmr(A, b::AbstractVector{FC};
                 c::AbstractVector{FC}=b, M=I, N=I, ldiv::Bool=false, atol::T=√eps(T),
                 rtol::T=√eps(T), itmax::Int=0, timemax::Float64=Inf, verbose::Int=0,
                 history::Bool=false, callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

```
(x, stats) = qmr(A, b, x0::AbstractVector; kwargs...)
```

QMR は初期推定値 `x0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

サイズ n の平方線形システム Ax = b を QMR を使用して解きます。

QMR はランチョスの双直交化プロセスに基づいており、2つの初期ベクトル `b` と `c` が必要です。関係 `bᴴc ≠ 0` が満たされなければならず、デフォルトでは `c = b` です。`A` がエルミートで `b = c` の場合、QMR は MINRES と同等です。QMR は前処理器が提供される場合、`adjoint(M)` と `adjoint(N)` のサポートが必要です。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :qmr` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

解の間でメモリを再利用するインプレースバリアントについては、[`qmr!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `n` の行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定値を表す長さ `n` のベクトル。

#### キーワード引数

  * `c`: ランチョスの双直交化プロセスに必要な長さ `n` の2番目の初期ベクトル;
  * `M`: 左前処理に使用されるサイズ `n` の非特異行列をモデル化する線形演算子;
  * `N`: 右前処理に使用されるサイズ `n` の非特異行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `2n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合、追加の詳細が表示されます (verbose > 0)。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力が記録されるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体に収集された実行中の統計。

#### 参考文献

  * R. W. Freund と N. M. Nachtigal, [*QMR : a quasi-minimal residual method for non-Hermitian linear systems*](https://doi.org/10.1007/BF01385726), Numerische mathematik, Vol. 60(1), pp. 315–339, 1991.
  * R. W. Freund と N. M. Nachtigal, [*An implementation of the QMR method based on coupled two-term recurrences*](https://doi.org/10.1137/0915022), SIAM Journal on Scientific Computing, Vol. 15(2), pp. 313–337, 1994.
  * A. Montoison と D. Orban, [*BiLQ: An Iterative Method for Nonsymmetric Linear Systems with a Quasi-Minimum Error Property*](https://doi.org/10.1137/19M1290991), SIAM Journal on Matrix Analysis and Applications, 41(3), pp. 1145–1166, 2020.
