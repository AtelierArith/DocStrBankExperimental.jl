```
(x, y, stats) = tricg(A, b::AbstractVector{FC}, c::AbstractVector{FC};
                      M=I, N=I, ldiv::Bool=false,
                      spd::Bool=false, snd::Bool=false,
                      flip::Bool=false, τ::T=one(T),
                      ν::T=-one(T), atol::T=√eps(T),
                      rtol::T=√eps(T), itmax::Int=0,
                      timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                      callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。 `FC` は `T` または `Complex{T}` です。

```
(x, y, stats) = tricg(A, b, c, x0::AbstractVector, y0::AbstractVector; kwargs...)
```

TriCG は初期推定値 `x0` と `y0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

行列 `A` の次元が m × n の場合、TriCG はエルミート線形系を解きます。

```
[ τE    A ] [ x ] = [ b ]
[  Aᴴ  νF ] [ y ]   [ c ],
```

サイズは (n+m) × (n+m) で、τ と ν は実数、E = M⁻¹ ≻ 0 および F = N⁻¹ ≻ 0 です。 `τ = 0` または `ν = 0` の場合、TriCG は故障する可能性があります。これらのケースでは TriMR を使用することをお勧めします。

デフォルトでは、TriCG は τ = 1 および ν = -1 でエルミートおよび準定義線形系を解きます。

TriCG は前処理された直交三重対角化プロセスと、前処理されたブロック・ランチョスプロセスとの関係に基づいています。

```
[ M   0 ]
[ 0   N ]
```

は、残差が測定される重み付きノルムを示します。 `M` と `N` が単位演算子である場合、ユークリッドノルムになります。

TriCG は `itmax` 回の反復が達成されるか、`‖rₖ‖ ≤ atol + ‖r₀‖ * rtol` の場合に停止します。 `atol` は絶対許容誤差で、`rtol` は相対許容誤差です。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :tricg` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

メモリを再利用するインプレースバリアントについては、[`tricg!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル;
  * `c`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定値を表す長さ `m` のベクトル;
  * `y0`: 解 `y` の初期推定値を表す長さ `n` のベクトル。

#### キーワード引数

  * `M`: 分割系の中心前処理に使用されるサイズ `m` のエルミート正定値行列をモデル化する線形演算子;
  * `N`: 分割系の中心前処理に使用されるサイズ `n` のエルミート正定値行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `spd`: `true` の場合、エルミートおよび正定値線形系のために `τ = 1` および `ν = 1` に設定します;
  * `snd`: `true` の場合、エルミートおよび負定値線形系のために `τ = -1` および `ν = -1` に設定します;
  * `flip`: `true` の場合、別の既知のエルミート準定義系のために `τ = -1` および `ν = 1` に設定します;
  * `τ` と `ν`: 分割エルミート線形系の対角スケーリング因子;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。 `itmax=0` の場合、デフォルトの反復回数は `m+n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は毎 `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ 残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力がログされるストリーム。

#### 出力引数

  * `x`: 長さ `m` の密なベクトル;
  * `y`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体に収集された実行中の統計。

#### 参考文献

  * A. Montoison と D. Orban, [*TriCG and TriMR: Two Iterative Methods for Symmetric Quasi-Definite Systems*](https://doi.org/10.1137/20M1363030), SIAM Journal on Scientific Computing, 43(4), pp. 2502–2525, 2021.

```
