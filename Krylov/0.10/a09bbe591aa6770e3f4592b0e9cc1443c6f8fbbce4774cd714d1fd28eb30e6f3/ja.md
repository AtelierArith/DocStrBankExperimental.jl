```
(x, stats) = fgmres(A, b::AbstractVector{FC};
                    memory::Int=20, M=I, N=I, ldiv::Bool=false,
                    restart::Bool=false, reorthogonalization::Bool=false,
                    atol::T=√eps(T), rtol::T=√eps(T), itmax::Int=0,
                    timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                    callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

```
(x, stats) = fgmres(A, b, x0::AbstractVector; kwargs...)
```

FGMRES は初期推定値 `x0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

サイズ n の線形システム Ax = b を FGMRES を使用して解きます。

FGMRES は最小残差を持つ近似解のシーケンスを計算します。FGMRES は、各反復で右前処理器の変更を許可する GMRES の変種です。

この実装では、左前処理器 M と柔軟な右前処理器 N を許可します。前処理器が「一定でない」状況は、緩和型手法、チェビシェフ反復、または他のクリロフ部分空間法が前処理器として使用される場合です。GMRES と比較して、算術的な追加コストは発生しませんが、メモリ要件はほぼ倍増します。したがって、右前処理器 N が一定の場合は GMRES を推奨します。

#### インターフェース

クリロフ法の間で簡単に切り替えるには、`method = :fgmres` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

メモリを再利用するインプレースバリアントについては、[`fgmres!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `n` の行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定値を表す長さ `n` のベクトル。

#### キーワード引数

  * `memory`: `restart = true` の場合、再起動されたバージョン FGMRES(k) が `k = memory` で使用されます。`restart = false` の場合、パラメータ `memory` は動的メモリ割り当てを制限するための反復回数のヒントとして使用されるべきです。反復回数が `memory` を超えると、追加のストレージが割り当てられます;
  * `M`: 左前処理に使用されるサイズ `n` の非特異行列をモデル化する線形演算子;
  * `N`: 右前処理に使用されるサイズ `n` の非特異行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `restart`: `memory` 回の反復後にメソッドを再起動します;
  * `reorthogonalization`: 新しいクリロフ基底のベクトルをすべての以前のベクトルに対して再直交化します;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `2n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は毎 `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ 残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、クリロフ法を終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力が記録されるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体に収集された実行中の統計。

#### 参考文献

  * Y. Saad, [*A Flexible Inner-Outer Preconditioned GMRES Algorithm*](https://doi.org/10.1137/0914028), SIAM Journal on Scientific Computing, Vol. 14(2), pp. 461–469, 1993.
