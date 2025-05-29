```
(x, stats) = cgls(A, b::AbstractVector{FC};
                  M=I, ldiv::Bool=false, radius::T=zero(T),
                  λ::T=zero(T), atol::T=√eps(T), rtol::T=√eps(T),
                  itmax::Int=0, timemax::Float64=Inf,
                  verbose::Int=0, history::Bool=false,
                  callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

正則化された線形最小二乗問題を解きます

```
minimize ‖b - Ax‖₂² + λ‖x‖₂²
```

サイズ m × n の問題を共役勾配 (CG) 法を使用して解きます。ここで λ ≥ 0 は正則化パラメータです。この方法は、正規方程式に CG を適用することと同等です。

```
(AᴴA + λI) x = Aᴴb
```

しかし、より安定しています。

CGLS はモノトニック残差 ‖r‖₂ を生成しますが、最適性残差 ‖Aᴴr‖₂ は生成しません。形式的には LSQR と同等ですが、わずかに精度が劣る場合がありますが、実装は簡単です。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :cgls` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

メモリを再利用するインプレースバリアントについては、[`cgls!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル。

#### キーワード引数

  * `M`: 前処理に使用されるサイズ `n` のエルミート正定値行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `radius`: `radius > 0` の場合、信頼領域制約 ‖x‖ ≤ `radius` を追加します。最適化のための信頼領域法でステップを計算するのに便利です;
  * `λ`: 正則化パラメータ;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `m+n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合 (verbose > 0)、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力がログされるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体に収集された実行中の統計。

#### 参考文献

  * M. R. Hestenes と E. Stiefel. [*Methods of conjugate gradients for solving linear systems*](https://doi.org/10.6028/jres.049.044), Journal of Research of the National Bureau of Standards, 49(6), pp. 409–436, 1952.
  * A. Björck, T. Elfving と Z. Strakos, [*Stability of Conjugate Gradient and Lanczos Methods for Linear Least Squares Problems*](https://doi.org/10.1137/S089547989631202X), SIAM Journal on Matrix Analysis and Applications, 19(3), pp. 720–736, 1998.
