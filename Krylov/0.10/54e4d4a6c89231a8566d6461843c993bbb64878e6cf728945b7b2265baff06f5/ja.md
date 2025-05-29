```
(x, stats) = bicgstab(A, b::AbstractVector{FC};
                      c::AbstractVector{FC}=b, M=I, N=I,
                      ldiv::Bool=false, atol::T=√eps(T),
                      rtol::T=√eps(T), itmax::Int=0,
                      timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                      callback=workspace->false, iostream::IO=kstdout)
```

`T`は`Float32`、`Float64`、または`BigFloat`のような`AbstractFloat`です。`FC`は`T`または`Complex{T}`です。

```
(x, stats) = bicgstab(A, b, x0::AbstractVector; kwargs...)
```

BICGSTABは、初期推定値`x0`からウォームスタートできます。`kwargs`は上記と同じキーワード引数です。

サイズnの平方線形システムAx = bをBICGSTABを使用して解きます。BICGSTABは、2つの初期ベクトル`b`と`c`を必要とします。関係`bᴴc ≠ 0`が満たされなければならず、デフォルトでは`c = b`です。

双共役勾配安定化法は、CGSのようなBiCGの変種ですが、CGSよりも滑らかな収束を得るためにAᴴシーケンスの異なる更新を使用します。

BICGSTABが停滞した場合、非対称平方システムの代替手法としてDQGMRESとBiLQを推奨します。

BICGSTABは、`itmax`回の反復が達成されるか、`‖rₖ‖ ≤ atol + ‖b‖ * rtol`が満たされると停止します。

#### インターフェース

Krylov法の間で簡単に切り替えるには、`method = :bicgstab`を使用して一般的なインターフェース[`krylov_solve`](@ref)を使用します。

解の間でメモリを再利用するインプレースバリアントについては、[`bicgstab!`](@ref)を参照してください。

#### 入力引数

  * `A`: 次元`n`の行列をモデル化する線形演算子;
  * `b`: 長さ`n`のベクトル。

#### オプション引数

  * `x0`: 解`x`の初期推定値を表す長さ`n`のベクトル。

#### キーワード引数

  * `c`: ランチョスの双直交化プロセスに必要な長さ`n`の2番目の初期ベクトル;
  * `M`: 左前処理に使用されるサイズ`n`の非特異行列をモデル化する線形演算子;
  * `N`: 右前処理に使用されるサイズ`n`の非特異行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が`ldiv!`または`mul!`を使用するかどうかを定義します;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0`の場合、デフォルトの反復回数は`2n`に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は`verbose`回の反復ごとに表示されます;
  * `history`: 残差ノルムやAᴴ残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)`として呼び出される関数またはファンクタで、Krylov法を終了すべき場合は`true`を返し、そうでない場合は`false`を返します;
  * `iostream`: 出力が記録されるストリーム。

#### 出力引数

  * `x`: 長さ`n`の密なベクトル;
  * `stats`: [`SimpleStats`](@ref)構造体で実行中に収集された統計。

#### 参考文献

  * H. A. van der Vorst, [*Bi-CGSTAB: A fast and smoothly converging variant of Bi-CG for the solution of nonsymmetric linear systems*](https://doi.org/10.1137/0913035), SIAM Journal on Scientific and Statistical Computing, 13(2), pp. 631–644, 1992.
  * G. L.G. Sleijpen and D. R. Fokkema, [*BiCGstab(ℓ) for linear equations involving unsymmetric matrices with complex spectrum*](https://etna.math.kent.edu/volumes/1993-2000/vol1/abstract.php?vol=1&pages=11-32), Electronic Transactions on Numerical Analysis, 1, pp. 11–32, 1993.
