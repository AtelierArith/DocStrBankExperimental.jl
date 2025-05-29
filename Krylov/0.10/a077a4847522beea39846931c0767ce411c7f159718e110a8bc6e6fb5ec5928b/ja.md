```
(x, stats) = lslq(A, b::AbstractVector{FC};
                  M=I, N=I, ldiv::Bool=false,
                  window::Int=5, transfer_to_lsqr::Bool=false,
                  sqd::Bool=false, λ::T=zero(T),
                  σ::T=zero(T), etol::T=√eps(T),
                  utol::T=√eps(T), btol::T=√eps(T),
                  conlim::T=1/√eps(T), atol::T=√eps(T),
                  rtol::T=√eps(T), itmax::Int=0,
                  timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                  callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。 `FC` は `T` または `Complex{T}` です。

正則化された線形最小二乗問題を解く

```
minimize ‖b - Ax‖₂² + λ²‖x‖₂²
```

サイズ m × n の LSLQ メソッドを使用して、ここで λ ≥ 0 は正則化パラメータです。LSLQ は、正規方程式に SYMMLQ を適用することと形式的に同等ですが、より安定しています。

`λ > 0` の場合、対称かつ準定義系のシステムを解きます

```
[ E      A ] [ r ]   [ b ]
[ Aᴴ  -λ²F ] [ x ] = [ 0 ],
```

ここで E と F は対称かつ正定値です。前処理器 M = E⁻¹ ≻ 0 および N = F⁻¹ ≻ 0 は線形演算子の形で提供できます。 `sqd=true` の場合、`λ` は共通の値 `1` に設定されます。

上記のシステムは、次の最適性条件を表します。

```
minimize ‖b - Ax‖²_E⁻¹ + λ²‖x‖²_F.
```

対称かつ正定値行列 `K` に対して、ベクトル `x` の K-ノルムは `‖x‖²_K = xᴴKx` です。LSLQ は次のように SYMMLQ を適用することと同等です `(AᴴE⁻¹A + λ²F)x = AᴴE⁻¹b` で `r = E⁻¹(b - Ax)` です。

`λ = 0` の場合、対称かつ不定のシステムを解きます。

```
[ E    A ] [ r ]   [ b ]
[ Aᴴ   0 ] [ x ] = [ 0 ].
```

上記のシステムは、次の最適性条件を表します。

```
minimize ‖b - Ax‖²_E⁻¹.
```

この場合、`N` はまだ指定でき、`x` と `Aᴴr` が測定される重み付きノルムを示します。 `r` は `E⁻¹(b - Ax)` を計算することで回復できます。

#### 主な特徴

  * 解の推定値は直交方向に沿って更新されます
  * 解の推定値 ‖xᴸₖ‖₂ のノルムは増加します
  * 誤差 ‖eₖ‖₂ := ‖xᴸₖ - x*‖₂ は減少します
  * LSLQ の反復から LSQR の反復に安価に移行することが可能です（誤差の観点では常に利点があります）
  * `A` がランク不足の場合、最小の最小二乗解を特定します

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :lslq` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

メモリを再利用するインプレースバリアントについては、[`lslq!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル。

#### キーワード引数

  * `M`: 拡張システムの中心前処理に使用されるサイズ `m` のエルミート正定値行列をモデル化する線形演算子;
  * `N`: 拡張システムの中心前処理に使用されるサイズ `n` のエルミート正定値行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `window`: 誤差の下限を蓄積するために使用される反復の数;
  * `transfer_to_lsqr`: 存在する場合、LSLQ ポイントから LSQR ポイントに転送します。転送は残差ノルムに基づいています;
  * `sqd`: `true` の場合、エルミート準定義系のシステムに対して `λ=1` に設定します;
  * `λ`: 正則化パラメータ;
  * `σ`: 最小の正の特異値 `σₘᵢₙ` に対する厳密な下限、すなわち `σ = (1-10⁻⁷)σₘᵢₙ`;
  * `etol`: 誤差の下限に基づく停止許容値;
  * `utol`: 誤差の上限に基づく停止許容値;
  * `btol`: ゼロ残差問題を検出するために使用される停止許容値;
  * `conlim`: 解が放棄される条件数の推定限界;
  * `atol`: 残差ノルムに基づく絶対停止許容値;
  * `rtol`: 残差ノルムに基づく相対停止許容値;
  * `itmax`: 最大反復回数。 `itmax=0` の場合、デフォルトの反復回数は `m+n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` 反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ 残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力がログされるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`LSLQStats`](@ref) 構造体に収集された実行中の統計。
  * `stats.err_lbnds` は LQ 誤差の下限のベクトル–-ベクトルは `window` がゼロに設定されている場合は空です
  * `stats.err_ubnds_lq` は LQ 誤差の上限のベクトル–-ベクトルは `σ == 0` がゼロに設定されている場合は空です
  * `stats.err_ubnds_cg` は CG 誤差の上限のベクトル–-ベクトルは `σ == 0` がゼロに設定されている場合は空です
  * `stats.error_with_bnd` は上限計算に誤差があったかどうかを示すブール値（キャンセル誤差、σ が大きすぎる ...）

#### 停止条件

反復は次の条件のいずれかが真であるとすぐに停止します。

  * 最適性残差が十分に小さい場合（`stats.status = "found approximate minimum least-squares solution"`）で、次のいずれかが成り立つ場合

      * ‖Aᴴr‖ / (‖A‖ ‖r‖) ≤ atol, または
      * 1 + ‖Aᴴr‖ / (‖A‖ ‖r‖) ≤ 1
  * おおよそのゼロ残差解が見つかった場合（`stats.status = "found approximate zero-residual solution"`）で、次のいずれかが成り立つ場合

      * ‖r‖ / ‖b‖ ≤ btol + atol ‖A‖ * ‖xᴸ‖ / ‖b‖, または
      * 1 + ‖r‖ / ‖b‖ ≤ 1
  * `A` の推定条件数が大きすぎる場合で、次のいずれかが成り立つ場合

      * 1/cond(A) ≤ 1/conlim (`stats.status = "condition number exceeds tolerance"`)、または
      * 1 + 1/cond(A) ≤ 1 (`stats.status = "condition number seems too large for this machine"`)
  * LQ 前方誤差の下限が etol * ‖xᴸ‖ より小さい
  * CG 前方誤差の上限が utol * ‖xᶜ‖ より小さい

#### 参考文献

  * R. Estrin, D. Orban and M. A. Saunders, [*Euclidean-norm error bounds for SYMMLQ and CG*](https://doi.org/10.1137/16M1094816), SIAM Journal on Matrix Analysis and Applications, 40(1), pp. 235–253, 2019.
  * R. Estrin, D. Orban and M. A. Saunders, [*LSLQ: An Iterative Method for Linear Least-Squares with an Error Minimization Property*](https://doi.org/10.1137/17M1113552), SIAM Journal on Matrix Analysis and Applications, 40(1), pp. 254–275, 2019.

```
