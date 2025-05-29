```
(x, stats) = usymqr(A, b::AbstractVector{FC}, c::AbstractVector{FC};
                    atol::T=√eps(T), rtol::T=√eps(T), itmax::Int=0,
                    timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                    callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

```
(x, stats) = usymqr(A, b, c, x0::AbstractVector; kwargs...)
```

USYMQR は初期推定値 `x0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

USYMQR はサイズ m × n の線形最小二乗問題 min ‖b - Ax‖² を解決します。USYMQR は Ax = b が一貫している場合にそれを解決します。

USYMQR は直交三重対角化プロセスに基づいており、2つの初期非ゼロベクトル `b` と `c` を必要とします。ベクトル `c` はプロセスを初期化するためだけに使用され、デフォルト値は `b` または `Aᴴb` で、`A` の形状に依存します。残差ノルム ‖b - Ax‖ は USYMQR で単調に減少します。`A` がエルミートで `b = c` の場合、QMR は MINRES と同等です。USYMQR は MINRES の一般化と見なされます。

これは、過小決定および過大決定問題にも適用できます。USYMQR は問題が一貫していない場合に最小ノルム解を見つけます。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :usymqr` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用してください。

メモリを再利用するインプレースバリアントについては、[`usymqr!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル;
  * `c`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定値を表す長さ `n` のベクトル。

#### キーワード引数

  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `m+n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力が記録されるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体で実行中に収集された統計。

#### 参考文献

  * M. A. Saunders, H. D. Simon, and E. L. Yip, [*Two Conjugate-Gradient-Type Methods for Unsymmetric Linear Equations*](https://doi.org/10.1137/0725052), SIAM Journal on Numerical Analysis, 25(4), pp. 927–940, 1988.
  * L. Reichel and Q. Ye, [*A generalized LSQR algorithm*](https://doi.org/10.1002/nla.611), Numerical Linear Algebra with Applications, 15(7), pp. 643–660, 2008.
  * A. Buttari, D. Orban, D. Ruiz and D. Titley-Peloquin, [*A tridiagonalization method for symmetric saddle-point and quasi-definite systems*](https://doi.org/10.1137/18M1194900), SIAM Journal on Scientific Computing, 41(5), pp. 409–432, 2019.
  * A. Montoison and D. Orban, [*BiLQ: An Iterative Method for Nonsymmetric Linear Systems with a Quasi-Minimum Error Property*](https://doi.org/10.1137/19M1290991), SIAM Journal on Matrix Analysis and Applications, 41(3), pp. 1145–1166, 2020.
