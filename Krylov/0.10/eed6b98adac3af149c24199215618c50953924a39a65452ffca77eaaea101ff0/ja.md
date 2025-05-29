```
(x, stats) = dqgmres(A, b::AbstractVector{FC};
                     memory::Int=20, M=I, N=I, ldiv::Bool=false,
                     reorthogonalization::Bool=false, atol::T=√eps(T),
                     rtol::T=√eps(T), itmax::Int=0,
                     timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                     callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

```
(x, stats) = dqgmres(A, b, x0::AbstractVector; kwargs...)
```

DQGMRES は初期推定値 `x0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

サイズ n の一貫した線形システム Ax = b を DQGMRES を使用して解きます。

DQGMRES アルゴリズムは不完全なアーノルディ直交化プロセスに基づいており、準最小残差特性を持つ近似解のシーケンスを計算します。

DQGMRES は新しい Krylov 基底のベクトルを `memory` の最も最近のベクトルに対してのみ直交化します。もし MINRES が `Ax = b` に対して適切に定義されていて `memory = 2` の場合、DQGMRES は理論的に MINRES と同等です。もし `k ≤ memory` であれば、`k` は反復回数で、DQGMRES は理論的に GMRES と同等です。それ以外の場合、DQGMRES は MINRES と GMRES の間を補間し、部分的な再直交化を伴う MINRES に似ています。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :dqgmres` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

解の間でメモリを再利用するインプレースバリアントについては、[`dqgmres!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `n` の行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定値を表す長さ `n` のベクトル。

#### キーワード引数

  * `memory`: 新しいベクトルを直交化するための Krylov 基底の最も最近のベクトルの数;
  * `M`: 左前処理に使用される次元 `n` の非特異行列をモデル化する線形演算子;
  * `N`: 右前処理に使用される次元 `n` の非特異行列をモデル化する線形演算子;
  * `reorthogonalization`: 新しい Krylov 基底のベクトルを `memory` の最も最近のベクトルに対して再直交化する;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義する;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `2n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集する;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力が記録されるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体に収集された実行中の統計。

#### 参考文献

  * Y. Saad と K. Wu, [*DQGMRES: a quasi minimal residual algorithm based on incomplete orthogonalization*](https://doi.org/10.1002/(SICI)1099-1506(199607/08)3:4%3C329::AID-NLA86%3E3.0.CO;2-8), Numerical Linear Algebra with Applications, Vol. 3(4), pp. 329–343, 1996.
