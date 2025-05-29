```
(x, stats) = cr(A, b::AbstractVector{FC};
                M=I, ldiv::Bool=false, radius::T=zero(T),
                linesearch::Bool=false, γ::T=√eps(T),
                atol::T=√eps(T), rtol::T=√eps(T), itmax::Int=0,
                timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。 `FC` は `T` または `Complex{T}` です。

```
(x, stats) = cr(A, b, x0::AbstractVector; kwargs...)
```

CR は初期推定値 `x0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

サイズ n のエルミート線形システム Ax = b を解くための Stiefel の共役残差法の切り捨てバージョン、または A が特異な場合の最小二乗問題 min ‖b - Ax‖。行列 A はエルミート半正定です。M は残差が測定される重み付きノルムも示します。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :cr` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

解の間でメモリを再利用するインプレースバリアントについては、[`cr!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `n` のエルミート正定行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定値を表す長さ `n` のベクトル。

#### キーワード引数

  * `M`: 中心化前処理に使用されるサイズ `n` のエルミート正定行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `radius`: `radius > 0` の場合、信頼領域制約 ‖x‖ ≤ `radius` を追加します。最適化のための信頼領域法でステップを計算するのに便利です;
  * `linesearch`: `true` の場合、解がラインサーチを伴う不正確なニュートン法で使用されることを示します。反曲が k > 0 の反復で検出された場合、反復 k-1 の解が返されます。反曲が反復 0 で検出された場合、右辺が返されます（すなわち、負の勾配）;
  * `γ`: 二次モデルの曲率が非正であることを判断するための許容誤差;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `2n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は毎 `verbose` 反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ 残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力がログされるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体で実行中に収集された統計。

#### 参考文献

  * M. R. Hestenes と E. Stiefel, [*Methods of conjugate gradients for solving linear systems*](https://doi.org/10.6028/jres.049.044), Journal of Research of the National Bureau of Standards, 49(6), pp. 409–436, 1952.
  * E. Stiefel, [*Relaxationsmethoden bester Strategie zur Losung linearer Gleichungssysteme*](https://doi.org/10.1007/BF02564277), Commentarii Mathematici Helvetici, 29(1), pp. 157–179, 1955.
  * D. G. Luenberger, [*The conjugate residual method for constrained minimization problems*](https://doi.org/10.1137/0707032), SIAM Journal on Numerical Analysis, 7(3), pp. 390–398, 1970.
  * M-A. Dahito と D. Orban, [*The Conjugate Residual Method in Linesearch and Trust-Region Methods*](https://doi.org/10.1137/18M1204255), SIAM Journal on Optimization, 29(3), pp. 1988–2025, 2019.
