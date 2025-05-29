```
(x, y, stats) = trilqr(A, b::AbstractVector{FC}, c::AbstractVector{FC};
                       transfer_to_usymcg::Bool=true, atol::T=√eps(T),
                       rtol::T=√eps(T), itmax::Int=0,
                       timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                       callback=workspace->false, iostream::IO=kstdout)
```

`T`は`AbstractFloat`であり、`Float32`、`Float64`、または`BigFloat`のいずれかです。`FC`は`T`または`Complex{T}`です。

```
(x, y, stats) = trilqr(A, b, c, x0::AbstractVector, y0::AbstractVector; kwargs...)
```

TriLQRは、初期推定値`x0`と`y0`からウォームスタートすることができ、`kwargs`は上記と同じキーワード引数です。

USYMLQとUSYMQRを組み合わせて随伴系を解きます。

```
[0  A] [y] = [b]
[Aᴴ 0] [x]   [c]
```

USYMLQはサイズm × nのプライマルシステム`Ax = b`を解くために使用されます。USYMQRはサイズn × mのデュアルシステム`Aᴴy = c`を解くために使用されます。

#### インターフェース

Krylovメソッド間で簡単に切り替えるには、`method = :trilqr`を使用して一般的なインターフェース[`krylov_solve`](@ref)を使用します。

メモリを再利用するインプレースバリアントについては、[trilqr!`](@ref)を参照してください。

#### 入力引数

  * `A`: 次元`m × n`の行列をモデル化する線形演算子;
  * `b`: 長さ`m`のベクトル;
  * `c`: 長さ`n`のベクトル。

#### オプション引数

  * `x0`: 解`x`の初期推定値を表す長さ`n`のベクトル;
  * `y0`: 解`y`の初期推定値を表す長さ`m`のベクトル。

#### キーワード引数

  * `transfer_to_usymcg`: USYMLQポイントからUSYMCGポイントへの転送が存在する場合。転送は残差ノルムに基づいています;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0`の場合、デフォルトの反復回数は`m+n`に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は`verbose`反復ごとに表示されます;
  * `history`: 残差ノルムやAᴴ-残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)`として呼び出される関数またはファンクタで、Krylovメソッドを終了すべき場合は`true`を返し、そうでない場合は`false`を返します;
  * `iostream`: 出力がログされるストリーム。

#### 出力引数

  * `x`: 長さ`n`の密なベクトル;
  * `y`: 長さ`m`の密なベクトル;
  * `stats`: [`AdjointStats`](@ref)構造体に収集された実行中の統計。

#### 参考文献

  * A. Montoison and D. Orban, [*BiLQ: An Iterative Method for Nonsymmetric Linear Systems with a Quasi-Minimum Error Property*](https://doi.org/10.1137/19M1290991), SIAM Journal on Matrix Analysis and Applications, 41(3), pp. 1145–1166, 2020.
