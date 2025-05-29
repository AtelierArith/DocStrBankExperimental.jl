```
(x, stats) = cg(A, b::AbstractVector{FC};
                M=I, ldiv::Bool=false, radius::T=zero(T),
                linesearch::Bool=false, atol::T=√eps(T),
                rtol::T=√eps(T), itmax::Int=0,
                timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。 `FC` は `T` または `Complex{T}` です。

```
(x, stats) = cg(A, b, x0::AbstractVector; kwargs...)
```

CG は初期推定値 `x0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

Hermitian 線形システム Ax = b のサイズ n を解くための共役勾配法。

この方法は、A が定義されていない場合でも中断しません。M は残差が測定される重み付きノルムも示します。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :cg` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

メモリを再利用するインプレースバリアントについては、[`cg!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `n` の Hermitian 正定値行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定値を表す長さ `n` のベクトル。

#### キーワード引数

  * `M`: 中心前処理に使用されるサイズ `n` の Hermitian 正定値行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `radius`: `radius > 0` の場合、信頼領域制約 ‖x‖ ≤ `radius` を追加します。最適化のための信頼領域法でステップを計算するのに便利です;
  * `linesearch`: `true` の場合、解がラインサーチを伴う不正確なニュートン法で使用されることを示します。イテレーション k > 0 で負の曲率が検出された場合、イテレーション k-1 の解が返されます。イテレーション 0 で負の曲率が検出された場合、右辺が返されます（すなわち、負の勾配）;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大イテレーション数。`itmax=0` の場合、デフォルトのイテレーション数は `2n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` イテレーションごとに表示されます;
  * `history`: 残差ノルムや Aᴴ 残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力がログされるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体で実行中に収集された統計。

#### 参考文献

  * M. R. Hestenes と E. Stiefel, [*Methods of conjugate gradients for solving linear systems*](https://doi.org/10.6028/jres.049.044), Journal of Research of the National Bureau of Standards, 49(6), pp. 409–436, 1952.
