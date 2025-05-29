```
(x, stats) = crls(A, b::AbstractVector{FC};
                  M=I, ldiv::Bool=false, radius::T=zero(T),
                  λ::T=zero(T), atol::T=√eps(T), rtol::T=√eps(T),
                  itmax::Int=0, timemax::Float64=Inf,
                  verbose::Int=0, history::Bool=false,
                  callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。 `FC` は `T` または `Complex{T}` です。

線形最小二乗問題を解く

```
minimize ‖b - Ax‖₂² + λ‖x‖₂²
```

サイズ m × n のものを共役残差 (CR) 法を使用して解きます。この方法は、正規方程式に MINRES を適用することと同等です。

```
(AᴴA + λI) x = Aᴴb.
```

この実装は残差 r := b - Ax を再帰的に計算します。

CRLS は単調な残差 ‖r‖₂ と最適性残差 ‖Aᴴr‖₂ を生成します。これは形式的には LSMR と同等ですが、実装が簡単である一方で、精度が大幅に低下する可能性があります。

#### インターフェース

Krylov 法の間で簡単に切り替えるには、`method = :crls` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用してください。

メモリを再利用するインプレースバリアントについては、[`crls!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル。

#### キーワード引数

  * `M`: 前処理に使用されるサイズ `n` のエルミート正定値行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `radius`: `radius > 0` の場合、信頼領域制約 ‖x‖ ≤ `radius` を追加します。最適化のための信頼領域法でステップを計算するのに便利です;
  * `λ`: 正則化パラメータ;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `m+n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合 (verbose > 0)、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov 法を終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力が記録されるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体に収集された実行中の統計。

#### 参考文献

  * D. C.-L. Fong, *Minimum-Residual Methods for Sparse, Least-Squares using Golubg-Kahan Bidiagonalization*, Ph.D. Thesis, Stanford University, 2011.
