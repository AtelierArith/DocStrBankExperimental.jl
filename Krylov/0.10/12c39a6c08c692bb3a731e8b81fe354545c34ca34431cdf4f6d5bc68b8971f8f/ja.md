```
(x, stats) = cg_lanczos_shift(A, b::AbstractVector{FC}, shifts::AbstractVector{T};
                              M=I, ldiv::Bool=false,
                              check_curvature::Bool=false, atol::T=√eps(T),
                              rtol::T=√eps(T), itmax::Int=0,
                              timemax::Float64=Inf, verbose::Int=0,
                              history::Bool=false, callback=workspace->false,
                              iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

シフトされたシステムのファミリーを解くための共役勾配法のランチョスバージョン

```
(A + αI) x = b  (α = α₁, ..., αₚ)
```

サイズ n の。A + αI が定義されていない場合でも、メソッドは *中止* しません。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :cg_lanczos_shift` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用してください。

メモリを再利用するインプレースバリアントについては、[`cg_lanczos_shift!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `n` のエルミート行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル;
  * `shifts`: 長さ `p` のベクトル。

#### キーワード引数

  * `M`: 中心前処理に使用されるサイズ `n` のエルミート正定値行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `check_curvature`: `true` の場合、探索方向に沿った二次関数の曲率が正であることを確認し、そうでない場合は中止します;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `2n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力がログされるストリーム。

#### 出力引数

  * `x`: 長さ `n` の各密なベクトルの `p` ベクトル;
  * `stats`: [`LanczosShiftStats`](@ref) 構造体で実行中に収集された統計。

#### 参考文献

  * A. Frommer と P. Maass, [*Fast CG-Based Methods for Tikhonov-Phillips Regularization*](https://doi.org/10.1137/S1064827596313310), SIAM Journal on Scientific Computing, 20(5), pp. 1831–1850, 1999.
  * C. C. Paige と M. A. Saunders, [*Solution of Sparse Indefinite Systems of Linear Equations*](https://doi.org/10.1137/0712047), SIAM Journal on Numerical Analysis, 12(4), pp. 617–629, 1975.
