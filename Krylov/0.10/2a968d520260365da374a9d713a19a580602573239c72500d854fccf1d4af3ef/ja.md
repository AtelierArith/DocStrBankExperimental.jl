```
(x, stats) = lsmr(A, b::AbstractVector{FC};
                  M=I, N=I, ldiv::Bool=false,
                  window::Int=5, sqd::Bool=false, λ::T=zero(T),
                  radius::T=zero(T), etol::T=√eps(T),
                  axtol::T=√eps(T), btol::T=√eps(T),
                  conlim::T=1/√eps(T), atol::T=zero(T),
                  rtol::T=zero(T), itmax::Int=0,
                  timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                  callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

正則化された線形最小二乗問題を解きます

```
minimize ‖b - Ax‖₂² + λ²‖x‖₂²
```

サイズ m × n の LSMR メソッドを使用して、ここで λ ≥ 0 は正則化パラメータです。LSMR は、正規方程式に MINRES を適用することと形式的に同等です

```
(AᴴA + λ²I) x = Aᴴb
```

（したがって CRLS にも）ですが、より安定しています。

LSMR は単調な残差 ‖r‖₂ と最適性残差 ‖Aᴴr‖₂ を生成します。これは CRLS と形式的に同等ですが、かなり正確である可能性があります。

LSMR は、任意の非ゼロベクトル `b` を用いて問題 `min ‖Aᴴx - b‖` を解くことによって、特異行列 A の零ベクトルを見つけるためにも使用できます。最小化点では、残差ベクトル `r = b - Aᴴx` は `Ar = 0` を満たします。

`λ > 0` の場合、対称かつ準定義の系を解きます

```
[ E      A ] [ r ]   [ b ]
[ Aᴴ  -λ²F ] [ x ] = [ 0 ],
```

ここで E と F は対称かつ正定です。前処理器 M = E⁻¹ ≻ 0 および N = F⁻¹ ≻ 0 は線形演算子の形で提供できます。`sqd=true` の場合、`λ` は共通の値 `1` に設定されます。

上記の系は次の最適性条件を表します

```
minimize ‖b - Ax‖²_E⁻¹ + λ²‖x‖²_F.
```

対称かつ正定の行列 `K` に対して、ベクトル `x` の K-ノルムは `‖x‖²_K = xᴴKx` です。LSMR は次のように MINRES を適用することと同等です `(AᴴE⁻¹A + λ²F)x = AᴴE⁻¹b` で `r = E⁻¹(b - Ax)` です。

`λ = 0` の場合、対称かつ不定の系を解きます

```
[ E    A ] [ r ]   [ b ]
[ Aᴴ   0 ] [ x ] = [ 0 ].
```

上記の系は次の最適性条件を表します

```
minimize ‖b - Ax‖²_E⁻¹.
```

この場合、`N` はまだ指定でき、`x` と `Aᴴr` が測定されるべき重み付きノルムを示します。`r` は `E⁻¹(b - Ax)` を計算することによって回復できます。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :lsmr` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

メモリを再利用するインプレースバリアントについては、[`lsmr!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル。

#### キーワード引数

  * `M`: 拡張系の中心前処理に使用されるサイズ `m` のエルミート正定行列をモデル化する線形演算子;
  * `N`: 拡張系の中心前処理に使用されるサイズ `n` のエルミート正定行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `window`: エラーの下限を蓄積するために使用される反復回数;
  * `sqd`: `true` の場合、エルミート準定系のために `λ=1` に設定します;
  * `λ`: 正則化パラメータ;
  * `radius`: `radius > 0` の場合、信頼領域制約 ‖x‖ ≤ `radius` を追加します。最適化のための信頼領域法でステップを計算するのに便利です;
  * `etol`: エラーの下限に基づく停止許容誤差;
  * `axtol`: 後方誤差に関する許容誤差;
  * `btol`: ゼロ残差問題を検出するために使用される停止許容誤差;
  * `conlim`: 解が放棄される条件数の推定値の制限;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `m+n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力が記録されるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`LsmrStats`](@ref) 構造体に収集された実行中の統計。

#### 参考文献

  * D. C.-L. Fong と M. A. Saunders, [*LSMR: An Iterative Algorithm for Sparse Least Squares Problems*](https://doi.org/10.1137/10079687X), SIAM Journal on Scientific Computing, 33(5), pp. 2950–2971, 2011.

```
