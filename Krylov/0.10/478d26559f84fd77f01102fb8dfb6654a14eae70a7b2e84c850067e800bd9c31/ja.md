```
(x, stats) = cgne(A, b::AbstractVector{FC};
                  N=I, ldiv::Bool=false,
                  λ::T=zero(T), atol::T=√eps(T),
                  rtol::T=√eps(T), itmax::Int=0,
                  timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                  callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

整合性のある線形システムを解きます

```
Ax + √λs = b
```

サイズ m × n のものを共役勾配法 (CG) を使用して解きます。ここで λ ≥ 0 は正則化パラメータです。この方法は、第二種の正規方程式に CG を適用することと同等です

```
(AAᴴ + λI) y = b
```

しかし、より安定しています。λ = 0 の場合、この方法は最小ノルム問題を解きます

min ‖x‖₂  s.t. Ax = b.

λ > 0 の場合、次の問題を解きます

```
min ‖(x,s)‖₂  s.t. Ax + √λs = b.
```

CGNE は単調な誤差 ‖x-x*‖₂ を生成しますが、残差 ‖r‖₂ は生成しません。形式的には CRAIG と同等ですが、わずかに精度が劣ることがありますが、実装は簡単です。解の x 部分のみが返されます。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :cgne` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

メモリを再利用するインプレースバリアントについては、[`cgne!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `m × n` の行列をモデル化する線形演算子;
  * `b`: 長さ `m` のベクトル。

#### キーワード引数

  * `N`: 前処理に使用されるサイズ `n` のエルミート正定値行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `λ`: 正則化パラメータ;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `m+n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合 (verbose > 0)、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力が記録されるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体で実行中に収集された統計。

#### 参考文献

  * J. E. Craig, [*The N-step iteration procedures*](https://doi.org/10.1002/sapm195534164), Journal of Mathematics and Physics, 34(1), pp. 64–73, 1955.
  * J. E. Craig, *Iterations Procedures for Simultaneous Equations*, Ph.D. Thesis, Department of Electrical Engineering, MIT, 1954.
