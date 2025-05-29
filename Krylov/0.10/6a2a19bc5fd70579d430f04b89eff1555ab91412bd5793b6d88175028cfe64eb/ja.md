```
(x, stats) = minres_qlp(A, b::AbstractVector{FC};
                        M=I, ldiv::Bool=false, Artol::T=√eps(T),
                        λ::T=zero(T), atol::T=√eps(T),
                        rtol::T=√eps(T), itmax::Int=0,
                        timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                        callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

```
(x, stats) = minres_qlp(A, b, x0::AbstractVector; kwargs...)
```

MINRES-QLP は初期推定値 `x0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

MINRES-QLP は、シフトパラメータ λ のもとで、サイズ n の特異不整合系 (A + λI)x = b に対して最小ノルム解を返す唯一のランチョスプロセスに基づく手法です。これはかなり複雑ですが、A が悪条件の場合、MINRES よりも信頼性が高いことがあります。

M は残差が測定される加重ノルムも示します。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :minres_qlp` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用してください。

メモリを再利用するインプレースバリアントについては、[`minres_qlp!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `n` のエルミート行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定値を表す長さ `n` のベクトル。

#### キーワード引数

  * `M`: 中心前処理に使用されるサイズ `n` のエルミート正定値行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `λ`: 正則化パラメータ;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `Artol`: Aᴴ-残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `2n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合、追加の詳細が表示されます (verbose > 0)。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力が記録されるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体に収集された実行中の統計。

#### 参考文献

  * S.-C. T. Choi, *特異線形方程式および最小二乗問題のための反復法*, Ph.D. 論文, ICME, スタンフォード大学, 2006.
  * S.-C. T. Choi, C. C. Paige および M. A. Saunders, [*MINRES-QLP: 無限または特異対称系のための Krylov 部分空間法*](https://doi.org/10.1137/100787921), SIAM Journal on Scientific Computing, Vol. 33(4), pp. 1810–1836, 2011.
  * S.-C. T. Choi および M. A. Saunders, [*アルゴリズム 937: 対称およびエルミート線形方程式および最小二乗問題のための MINRES-QLP*](https://doi.org/10.1145/2527267), ACM Transactions on Mathematical Software, 40(2), pp. 1–12, 2014.
