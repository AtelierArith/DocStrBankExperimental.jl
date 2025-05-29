```
(x, y, stats) = bilqr(A, b::AbstractVector{FC}, c::AbstractVector{FC};
                      transfer_to_bicg::Bool=true, atol::T=√eps(T),
                      rtol::T=√eps(T), itmax::Int=0,
                      timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                      callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。 `FC` は `T` または `Complex{T}` です。

```
(x, y, stats) = bilqr(A, b, c, x0::AbstractVector, y0::AbstractVector; kwargs...)
```

BiLQR は初期推定値 `x0` と `y0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

BiLQ と QMR を組み合わせて随伴系を解きます。

```
[0  A] [y] = [b]
[Aᴴ 0] [x]   [c]
```

関係 `bᴴc ≠ 0` が満たされなければなりません。BiLQ はサイズ n の原始系 `Ax = b` を解くために使用されます。QMR はサイズ n の双対系 `Aᴴy = c` を解くために使用されます。

#### インターフェース

Krylov メソッド間を簡単に切り替えるには、`method = :bilqr` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

メモリを再利用するインプレースバリアントについては、[`bilqr!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `n` の行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル;
  * `c`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定値を表す長さ `n` のベクトル;
  * `y0`: 解 `y` の初期推定値を表す長さ `n` のベクトル。

#### キーワード引数

  * `transfer_to_bicg`: BiLQ ポイントから BiCG ポイントへの転送、存在する場合。転送は残差ノルムに基づいています;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `2n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力が記録されるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `y`: 長さ `n` の密なベクトル;
  * `stats`: [`AdjointStats`](@ref) 構造体において実行中に収集された統計。

#### 参考文献

  * A. Montoison と D. Orban, [*BiLQ: An Iterative Method for Nonsymmetric Linear Systems with a Quasi-Minimum Error Property*](https://doi.org/10.1137/19M1290991), SIAM Journal on Matrix Analysis and Applications, 41(3), pp. 1145–1166, 2020.
