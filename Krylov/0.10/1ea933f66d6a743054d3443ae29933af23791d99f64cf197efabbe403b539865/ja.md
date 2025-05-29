```
(x, y, stats) = craig(A, b::AbstractVector{FC};
                      M=I, N=I, ldiv::Bool=false,
                      transfer_to_lsqr::Bool=false, sqd::Bool=false,
                      λ::T=zero(T), btol::T=√eps(T),
                      conlim::T=1/√eps(T), atol::T=√eps(T),
                      rtol::T=√eps(T), itmax::Int=0,
                      timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                      callback=workspace->false, iostream::IO=kstdout)
```

`T`は`AbstractFloat`であり、`Float32`、`Float64`、または`BigFloat`のいずれかです。`FC`は`T`または`Complex{T}`です。

λ ≥ 0の正則化パラメータを用いて、サイズm × nの一貫した線形システム

```
Ax + λ²y = b
```

の最小ノルム解を求めます。この方法はCGNEと同等ですが、より安定しています。

Ax = bの形のシステムに対して、Craigの方法はAAᴴy = bにCGを適用し、x = Aᴴyを回復することに相当します。yは最小ノルム問題のラグランジュ乗数であることに注意してください。

```
minimize ‖x‖  s.t.  Ax = b.
```

`λ > 0`の場合、CRAIGは対称かつ準定義のシステムを解きます。

```
[ -F     Aᴴ ] [ x ]   [ 0 ]
[  A   λ²E  ] [ y ] = [ b ],
```

ここでEとFは対称かつ正定です。前処理器M = E⁻¹ ≻ 0およびN = F⁻¹ ≻ 0は線形演算子の形で提供できます。`sqd=true`の場合、`λ`は共通の値`1`に設定されます。

上記のシステムは次の最適性条件を表します。

```
min ‖x‖²_F + λ²‖y‖²_E  s.t.  Ax + λ²Ey = b.
```

対称かつ正定の行列`K`に対して、ベクトル`x`のKノルムは`‖x‖²_K = xᴴKx`です。CRAIGは次のようにCGを適用することに相当します。

```
(AF⁻¹Aᴴ + λ²E)y = b
```

ここで`Fx = Aᴴy`です。

`λ = 0`の場合、CRAIGは対称かつ不定のシステムを解きます。

```
[ -F   Aᴴ ] [ x ]   [ 0 ]
[  A   0  ] [ y ] = [ b ].
```

上記のシステムは次の最適性条件を表します。

```
minimize ‖x‖²_F  s.t.  Ax = b.
```

この場合、`M`はまだ指定でき、残差が測定される加重ノルムを示します。

この実装では、解のx部分とy部分の両方が返されます。

#### インターフェース

Krylovメソッド間で簡単に切り替えるには、`method = :craig`を使用して一般的なインターフェース[`krylov_solve`](@ref)を使用します。

メモリを再利用するインプレースバリアントについては、[`craig!`](@ref)を参照してください。

#### 入力引数

  * `A`: 次元`m × n`の行列をモデル化する線形演算子;
  * `b`: 長さ`m`のベクトル。

#### キーワード引数

  * `M`: 拡張システムの中心前処理に使用されるサイズ`m`のエルミート正定行列をモデル化する線形演算子;
  * `N`: 拡張システムの中心前処理に使用されるサイズ`n`のエルミート正定行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が`ldiv!`または`mul!`を使用するかどうかを定義します;
  * `transfer_to_lsqr`: 存在する場合、LSLQポイントからLSQRポイントに転送します。転送は残差ノルムに基づいています;
  * `sqd`: `true`の場合、エルミート準定義システムのために`λ=1`に設定します;
  * `λ`: 正則化パラメータ;
  * `btol`: ゼロ残差問題を検出するために使用される停止許容誤差;
  * `conlim`: 解が放棄される条件数の推定値の制限;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0`の場合、デフォルトの反復回数は`m+n`に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は`verbose`反復ごとに表示されます;
  * `history`: 残差ノルムやAᴴ残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)`として呼び出される関数またはファンクタで、Krylovメソッドを終了すべき場合は`true`を返し、そうでない場合は`false`を返します;
  * `iostream`: 出力がログされるストリーム。

#### 出力引数

  * `x`: 長さ`n`の密なベクトル;
  * `y`: 長さ`m`の密なベクトル;
  * `stats`: [`SimpleStats`](@ref)構造体に収集された実行統計。

#### 参考文献

  * J. E. Craig, [*The N-step iteration procedures*](https://doi.org/10.1002/sapm195534164), Journal of Mathematics and Physics, 34(1-4), pp. 64–73, 1955.
  * C. C. Paige and M. A. Saunders, [*LSQR: An Algorithm for Sparse Linear Equations and Sparse Least Squares*](https://doi.org/10.1145/355984.355989), ACM Transactions on Mathematical Software, 8(1), pp. 43–71, 1982.
  * M. A. Saunders, [*Solutions of Sparse Rectangular Systems Using LSQR and CRAIG*](https://doi.org/10.1007/BF01739829), BIT Numerical Mathematics, 35(4), pp. 588–604, 1995.
