```
(x, y, stats) = craigmr(A, b::AbstractVector{FC};
                        M=I, N=I, ldiv::Bool=false,
                        sqd::Bool=false, λ::T=zero(T), atol::T=√eps(T),
                        rtol::T=√eps(T), itmax::Int=0,
                        timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                        callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

次の一貫した線形システムを解きます

```
Ax + λ²y = b
```

サイズ m × n の CRAIGMR メソッドを使用します。ここで λ ≥ 0 は正則化パラメータです。この方法は、次のような第二種の正規方程式に共役残差法を適用することに相当します。

```
(AAᴴ + λ²I) y = b
```

ただし、より安定しています。λ = 0 の場合、この方法は最小ノルム問題を解きます。

```
min ‖x‖  s.t.  x ∈ argmin ‖Ax - b‖.
```

`λ > 0` の場合、CRAIGMR は対称かつ準定義のシステムを解きます。

```
[ -F    Aᴴ ] [ x ]   [ 0 ]
[  A  λ²E  ] [ y ] = [ b ],
```

ここで E と F は対称かつ正定です。前処理器 M = E⁻¹ ≻ 0 および N = F⁻¹ ≻ 0 は線形演算子の形で提供できます。`sqd=true` の場合、`λ` は共通の値 `1` に設定されます。

上記のシステムは次の最適性条件を表します。

```
min ‖x‖²_F + λ²‖y‖²_E  s.t.  Ax + λ²Ey = b.
```

対称かつ正定の行列 `K` に対して、ベクトル `x` の K-ノルムは `‖x‖²_K = xᴴKx` です。CRAIGMR は次のように MINRES を `(AF⁻¹Aᴴ + λ²E)y = b` に適用することに相当します。ここで `Fx = Aᴴy` です。

`λ = 0` の場合、CRAIGMR は対称かつ不定のシステムを解きます。

```
[ -F   Aᴴ ] [ x ]   [ 0 ]
[  A   0  ] [ y ] = [ b ].
```

上記のシステムは次の最適性条件を表します。

```
min ‖x‖²_F  s.t.  Ax = b.
```

この場合、`M` はまだ指定でき、残差が測定される重み付きノルムを示します。

CRAIGMR は単調な残差 ‖r‖₂ を生成します。形式的には CRMR に相当しますが、わずかにより正確で、実装が複雑です。解の x 部分と y 部分の両方が返されます。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :craigmr` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

メモリを再利用するインプレースバリアントについては、[`craigmr!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル。

#### キーワード引数

  * `M`: 拡張システムの中心前処理に使用されるサイズ `m` のエルミート正定行列をモデル化する線形演算子;
  * `N`: 拡張システムの中心前処理に使用されるサイズ `n` のエルミート正定行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `sqd`: `true` の場合、エルミート準定義システムのために `λ=1` に設定します;
  * `λ`: 正則化パラメータ;
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
  * `y`: 長さ `m` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体に収集された実行中の統計。

#### 参考文献

  * D. Orban と M. Arioli. [*Iterative Solution of Symmetric Quasi-Definite Linear Systems*](https://doi.org/10.1137/1.9781611974737), Spotlights の第 3 巻。SIAM, Philadelphia, PA, 2017.
  * D. Orban, [*The Projected Golub-Kahan Process for Constrained, Linear Least-Squares Problems*](https://dx.doi.org/10.13140/RG.2.2.17443.99360). Cahier du GERAD G-2014-15, 2014.
