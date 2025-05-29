```
(x, stats) = cgs(A, b::AbstractVector{FC};
                 c::AbstractVector{FC}=b, M=I, N=I,
                 ldiv::Bool=false, atol::T=√eps(T),
                 rtol::T=√eps(T), itmax::Int=0,
                 timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                 callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。 `FC` は `T` または `Complex{T}` です。

```
(x, stats) = cgs(A, b, x0::AbstractVector; kwargs...)
```

CGS は初期推定値 `x0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

サイズ n の一貫した線形システム Ax = b を CGS を使用して解きます。 CGS には初期ベクトル `b` と `c` の 2 つが必要です。関係 `bᴴc ≠ 0` が満たされなければならず、デフォルトでは `c = b` です。

「スパース線形システムのための反復法 (Y. Saad)」から：

«この手法は共役勾配法の多項式バリアントに基づいています。いわゆる双共役勾配法 (BCG) アルゴリズムに関連していますが、随伴行列-ベクトルの乗算は含まれておらず、期待される収束率は BCG アルゴリズムの約 2 倍です。

共役勾配二乗アルゴリズムは多くのケースで非常によく機能します。しかし、1 つの難しさは、多項式が二乗されるため、丸め誤差が標準 BCG アルゴリズムよりもより有害になる傾向があることです。特に、残差ベクトルの非常に高い変動は、計算された残差ノルムが不正確になる原因となることがよくあります。

TFQMR と BICGSTAB はこの問題を解決するために開発されました。»

#### インターフェース

Krylov 法の間で簡単に切り替えるには、`method = :cgs` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

解の間でメモリを再利用するインプレースバリアントについては、[`cgs!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `n` の行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定値を表す長さ `n` のベクトル。

#### キーワード引数

  * `c`: ランチョス双直交化プロセスに必要な長さ `n` の第 2 の初期ベクトル;
  * `M`: 左前処理に使用されるサイズ `n` の非特異行列をモデル化する線形演算子;
  * `N`: 右前処理に使用されるサイズ `n` の非特異行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `2n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合 (verbose > 0)、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov 法を終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力が記録されるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体に収集された実行中の統計。

#### 参考文献

  * P. Sonneveld, [*CGS, A Fast Lanczos-Type Solver for Nonsymmetric Linear systems*](https://doi.org/10.1137/0910004), SIAM Journal on Scientific and Statistical Computing, 10(1), pp. 36–52, 1989.
