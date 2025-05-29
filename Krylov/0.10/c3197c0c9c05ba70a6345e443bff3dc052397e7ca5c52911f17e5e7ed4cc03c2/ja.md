```
(x, stats) = usymlq(A, b::AbstractVector{FC}, c::AbstractVector{FC};
                    transfer_to_usymcg::Bool=true, atol::T=√eps(T),
                    rtol::T=√eps(T), itmax::Int=0,
                    timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                    callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

```
(x, stats) = usymlq(A, b, c, x0::AbstractVector; kwargs...)
```

USYMLQ は初期推定値 `x0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

USYMLQ は、サイズ m × n の一貫した線形システム Ax = b の最小ノルム解を決定します。

USYMLQ は直交三重対角化プロセスに基づいており、2つの初期非ゼロベクトル `b` と `c` を必要とします。ベクトル `c` はプロセスの初期化にのみ使用され、デフォルト値は `b` または `Aᴴb` で、`A` の形状に依存します。誤差ノルム ‖x - x*‖ は USYMLQ で単調に減少します。`A` がエルミートで `b = c` の場合、USYMLQ は SYMMLQ と同等です。USYMLQ は SYMMLQ の一般化と見なされます。

これは、過小決定および過大決定問題にも適用できます。すべての場合において、問題は一貫している必要があります。

#### インターフェース

Krylov メソッド間を簡単に切り替えるには、`method = :usymlq` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用してください。

メモリを再利用するインプレースバリアントについては、[`usymlq!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル;
  * `c`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定値を表す長さ `n` のベクトル。

#### キーワード引数

  * `transfer_to_usymcg`: USYMLQ ポイントから USYMCG ポイントへの転送、存在する場合。転送は残差ノルムに基づいています;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `m+n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力がログされるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体で実行中に収集された統計。

#### 参考文献

  * M. A. Saunders, H. D. Simon, and E. L. Yip, [*Two Conjugate-Gradient-Type Methods for Unsymmetric Linear Equations*](https://doi.org/10.1137/0725052), SIAM Journal on Numerical Analysis, 25(4), pp. 927–940, 1988.
  * A. Buttari, D. Orban, D. Ruiz and D. Titley-Peloquin, [*A tridiagonalization method for symmetric saddle-point and quasi-definite systems*](https://doi.org/10.1137/18M1194900), SIAM Journal on Scientific Computing, 41(5), pp. 409–432, 2019.
  * A. Montoison and D. Orban, [*BiLQ: An Iterative Method for Nonsymmetric Linear Systems with a Quasi-Minimum Error Property*](https://doi.org/10.1137/19M1290991), SIAM Journal on Matrix Analysis and Applications, 41(3), pp. 1145–1166, 2020.
