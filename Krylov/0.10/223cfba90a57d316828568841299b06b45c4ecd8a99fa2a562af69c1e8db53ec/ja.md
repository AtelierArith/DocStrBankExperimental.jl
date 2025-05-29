```
(x, y, stats) = lnlq(A, b::AbstractVector{FC};
                     M=I, N=I, ldiv::Bool=false,
                     transfer_to_craig::Bool=true,
                     sqd::Bool=false, λ::T=zero(T),
                     σ::T=zero(T), utolx::T=√eps(T),
                     utoly::T=√eps(T), atol::T=√eps(T),
                     rtol::T=√eps(T), itmax::Int=0,
                     timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                     callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。 `FC` は `T` または `Complex{T}` です。

LNLQ メソッドを使用して、サイズ m × n の一貫した線形システム

```
Ax + λ²y = b
```

の最小ノルム解を見つけます。ここで、λ ≥ 0 は正則化パラメータです。

Ax = b の形のシステムに対して、LNLQ メソッドは AAᴴy = b に SYMMLQ を適用し、x = Aᴴy を回復することと同等ですが、より安定しています。y は最小ノルム問題のラグランジュ乗数です。

```
minimize ‖x‖  s.t.  Ax = b.
```

`λ > 0` の場合、LNLQ は対称かつ準定義のシステムを解決します。

```
[ -F    Aᴴ ] [ x ]   [ 0 ]
[  A  λ²E  ] [ y ] = [ b ],
```

ここで、E と F は対称かつ正定です。前処理器 M = E⁻¹ ≻ 0 および N = F⁻¹ ≻ 0 は線形演算子の形で提供できます。`sqd=true` の場合、`λ` は共通の値 `1` に設定されます。

上記のシステムは、次の最適性条件を表します。

```
min ‖x‖²_F + λ²‖y‖²_E  s.t.  Ax + λ²Ey = b.
```

対称かつ正定の行列 `K` に対して、ベクトル `x` の K-ノルムは `‖x‖²_K = xᴴKx` です。LNLQ は次のように SYMMLQ を適用することと同等です。

```
(AF⁻¹Aᴴ + λ²E)y = b
```

ここで `Fx = Aᴴy` です。

`λ = 0` の場合、LNLQ は対称かつ不定のシステムを解決します。

```
[ -F   Aᴴ ] [ x ]   [ 0 ]
[  A   0  ] [ y ] = [ b ].
```

上記のシステムは、次の最適性条件を表します。

```
minimize ‖x‖²_F  s.t.  Ax = b.
```

この場合、`M` はまだ指定でき、残差が測定される加重ノルムを示します。

この実装では、解の x 部分と y 部分の両方が返されます。

`utolx` と `utoly` は、解への距離 ‖x-x*‖ および ‖y-y*‖ の上限に対する許容誤差です。この上限は λ>0 または σ>0 の場合に有効であり、σ は最小の正の特異値よりも厳密に小さくする必要があります。例えば、σ:=(1-1e-7)σₘᵢₙ です。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :lnlq` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

メモリを再利用するインプレースバリアントについては、[`lnlq!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル。

#### キーワード引数

  * `M`: 拡張システムの中心前処理に使用されるサイズ `m` のエルミート正定行列をモデル化する線形演算子;
  * `N`: 拡張システムの中心前処理に使用されるサイズ `n` のエルミート正定行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `transfer_to_craig`: LNLQ ポイントから CRAIG ポイントへの転送、存在する場合。転送は残差ノルムに基づいています;
  * `sqd`: `true` の場合、エルミート準定義システムのために `λ=1` に設定します;
  * `λ`: 正則化パラメータ;
  * `σ`: 最小の正の特異値 `σₘᵢₙ` に対する厳密な下限、例えば `σ = (1-10⁻⁷)σₘᵢₙ`;
  * `utolx`: 解への距離 `‖x-x*‖` の上限に対する許容誤差;
  * `utoly`: 解への距離 `‖y-y*‖` の上限に対する許容誤差;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `m+n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ 残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力がログされるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `y`: 長さ `m` の密なベクトル;
  * `stats`: [`LNLQStats`](@ref) 構造体に収集された実行中の統計。

#### 参考文献

  * R. Estrin, D. Orban, M.A. Saunders, [*LNLQ: An Iterative Method for Least-Norm Problems with an Error Minimization Property*](https://doi.org/10.1137/18M1194948), SIAM Journal on Matrix Analysis and Applications, 40(3), pp. 1102–1124, 2019.

```
