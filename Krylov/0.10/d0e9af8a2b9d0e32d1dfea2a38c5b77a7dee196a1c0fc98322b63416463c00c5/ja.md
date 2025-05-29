```
(x, stats) = lsqr(A, b::AbstractVector{FC};
                  M=I, N=I, ldiv::Bool=false,
                  window::Int=5, sqd::Bool=false, λ::T=zero(T),
                  radius::T=zero(T), etol::T=√eps(T),
                  axtol::T=√eps(T), btol::T=√eps(T),
                  conlim::T=1/√eps(T), atol::T=zero(T),
                  rtol::T=zero(T), itmax::Int=0,
                  timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                  callback=workspace->false, iostream::IO=kstdout)
```

`T` は `AbstractFloat` であり、`Float32`、`Float64` または `BigFloat` のいずれかです。 `FC` は `T` または `Complex{T}` です。

正則化された線形最小二乗問題を解きます

```
minimize ‖b - Ax‖₂² + λ²‖x‖₂²
```

サイズ m × n の問題を LSQR 法を使用して解きます。ここで λ ≥ 0 は正則化パラメータです。LSQR は、正規方程式に CG を適用することに形式的に相当します

```
(AᴴA + λ²I) x = Aᴴb
```

（したがって CGLS にも相当します）が、より安定しています。

LSQR は単調な残差 ‖r‖₂ を生成しますが、最適性残差 ‖Aᴴr‖₂ は生成しません。形式的には CGLS に相当しますが、わずかにより正確である可能性があります。

`λ > 0` の場合、LSQR は対称かつ準定義系を解きます

```
[ E      A ] [ r ]   [ b ]
[ Aᴴ  -λ²F ] [ x ] = [ 0 ],
```

ここで E と F は対称かつ正定義です。前処理器 M = E⁻¹ ≻ 0 および N = F⁻¹ ≻ 0 は線形演算子の形で提供できます。`sqd=true` の場合、`λ` は共通の値 `1` に設定されます。

上記の系は次の最適性条件を表します

```
minimize ‖b - Ax‖²_E⁻¹ + λ²‖x‖²_F.
```

対称かつ正定義の行列 `K` に対して、ベクトル `x` の K-ノルムは `‖x‖²_K = xᴴKx` です。LSQR は次の式に対して CG を適用することに相当します `(AᴴE⁻¹A + λ²F)x = AᴴE⁻¹b` で、`r = E⁻¹(b - Ax)` です。

`λ = 0` の場合、対称かつ不定系を解きます

```
[ E    A ] [ r ]   [ b ]
[ Aᴴ   0 ] [ x ] = [ 0 ].
```

上記の系は次の最適性条件を表します

```
minimize ‖b - Ax‖²_E⁻¹.
```

この場合、`N` はまだ指定でき、`x` と `Aᴴr` が測定されるべき重み付きノルムを示します。`r` は `E⁻¹(b - Ax)` を計算することで回復できます。

#### インターフェース

Krylov 法の間で簡単に切り替えるには、`method = :lsqr` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

メモリを再利用するインプレースバリアントについては、[`lsqr!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル。

#### キーワード引数

  * `M`: 拡張系の中心前処理に使用されるサイズ `m` のエルミート正定義行列をモデル化する線形演算子;
  * `N`: 拡張系の中心前処理に使用されるサイズ `n` のエルミート正定義行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `window`: エラーの下限を蓄積するために使用される反復回数;
  * `sqd`: `true` の場合、エルミート準定義系のために `λ=1` に設定します;
  * `λ`: 正則化パラメータ;
  * `radius`: `radius > 0` の場合、信頼領域制約 ‖x‖ ≤ `radius` を追加します。最適化のための信頼領域法でステップを計算するのに便利です;
  * `etol`: エラーの下限に基づく停止許容誤差;
  * `axtol`: 後方誤差に対する許容誤差;
  * `btol`: ゼロ残差問題を検出するために使用される停止許容誤差;
  * `conlim`: 解が放棄される条件数の推定値の制限;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `m+n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov 法を終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力がログされるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体に収集された実行統計。

#### 参考文献

  * C. C. Paige と M. A. Saunders, [*LSQR: An Algorithm for Sparse Linear Equations and Sparse Least Squares*](https://doi.org/10.1145/355984.355989), ACM Transactions on Mathematical Software, 8(1), pp. 43–71, 1982.

```
