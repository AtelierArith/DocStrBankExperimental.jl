```
(x, y, stats) = gpmr(A, B, b::AbstractVector{FC}, c::AbstractVector{FC};
                     memory::Int=20, C=I, D=I, E=I, F=I,
                     ldiv::Bool=false, gsp::Bool=false,
                     λ::FC=one(FC), μ::FC=one(FC),
                     reorthogonalization::Bool=false, atol::T=√eps(T),
                     rtol::T=√eps(T), itmax::Int=0,
                     timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                     callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

```
(x, y, stats) = gpmr(A, B, b, c, x0::AbstractVector, y0::AbstractVector; kwargs...)
```

GPMR は初期推定値 `x0` と `y0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

次の次元の行列 `A` (m × n) と `B` (n × m) が与えられた場合、GPMR は非エルミート分割線形システムを解きます。

```
[ λIₘ   A  ] [ x ] = [ b ]
[  B   μIₙ ] [ y ]   [ c ],
```

サイズは (n+m) × (n+m) で、λ と μ は実数または複素数です。`A` は任意の形状を持つことができ、`B` は `Aᴴ` の形状を持ちます。`A` と `B` はどちらもゼロであってはなりません。

この実装は左および右のブロック対角前処理器を許可します。

```
[ C    ] [ λM   A ] [ E    ] [ E⁻¹x ] = [ Cb ]
[    D ] [  B  μN ] [    F ] [ F⁻¹y ]   [ Dc ],
```

そして次のように解くことができます。

```
[ λM   A ] [ x ] = [ b ]
[  B  μN ] [ y ]   [ c ]
```

`CE = M⁻¹` および `DF = N⁻¹` のときです。

デフォルトでは、GPMR は `λ = 1` および `μ = 1` で非対称線形システムを解きます。

GPMR は直交ヘッセンベルグ削減プロセスとブロック・アーノルディプロセスとの関係に基づいています。残差ノルム ‖rₖ‖ は GPMR で単調減少します。

GPMR は `itmax` 回の反復が達成されるか、`‖rₖ‖ ≤ atol + ‖r₀‖ * rtol` のときに停止します。`atol` は絶対許容誤差で、`rtol` は相対許容誤差です。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :gpmr` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用してください。

メモリを再利用するインプレースバリアントについては、[`gpmr!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `B`: 次元 `n × m` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル;
  * `c`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定を表す長さ `m` のベクトル;
  * `y0`: 解 `y` の初期推定を表す長さ `n` のベクトル。

#### キーワード引数

  * `memory`: `restart = true` の場合、再起動されたバージョン GPMR(k) が `k = memory` で使用されます。`restart = false` の場合、パラメータ `memory` は動的メモリ割り当てを制限するための反復回数のヒントとして使用されるべきです。反復回数が `memory` を超えると、追加のストレージが割り当てられます;
  * `C`: サイズ `m` の非特異行列をモデル化する線形演算子で、ブロック対角左前処理器の最初の項を表します;
  * `D`: サイズ `n` の非特異行列をモデル化する線形演算子で、ブロック対角左前処理器の2番目の項を表します;
  * `E`: サイズ `m` の非特異行列をモデル化する線形演算子で、ブロック対角右前処理器の最初の項を表します;
  * `F`: サイズ `n` の非特異行列をモデル化する線形演算子で、ブロック対角右前処理器の2番目の項を表します;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `gsp`: `true` の場合、一般化サドルポイントシステムのために `λ = 1` および `μ = 0` に設定します;
  * `λ` と `μ`: 分割線形システムの対角スケーリング係数;
  * `reorthogonalization`: 新しいKrylov基底のベクトルをすべての以前のベクトルに対して再直交化します;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `m+n` に設定されます;
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

  * A. Montoison と D. Orban, [*GPMR: An Iterative Method for Unsymmetric Partitioned Linear Systems*](https://doi.org/10.1137/21M1459265), SIAM Journal on Matrix Analysis and Applications, 44(1), pp. 293–311, 2023.

```
