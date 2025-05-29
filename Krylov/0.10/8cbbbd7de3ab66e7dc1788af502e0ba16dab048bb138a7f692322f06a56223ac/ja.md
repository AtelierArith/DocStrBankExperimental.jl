```
(x, stats) = diom(A, b::AbstractVector{FC};
                  memory::Int=20, M=I, N=I, ldiv::Bool=false,
                  reorthogonalization::Bool=false, atol::T=√eps(T),
                  rtol::T=√eps(T), itmax::Int=0,
                  timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                  callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

```
(x, stats) = diom(A, b, x0::AbstractVector; kwargs...)
```

DIOM は初期推定値 `x0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

DIOM を使用してサイズ n の一貫した線形システム Ax = b を解きます。

DIOM は新しいベクトルを Krylov 基底の `memory` 個の最近のベクトルに対してのみ直交化します。もし CG が `Ax = b` に対して適切に定義されていて `memory = 2` の場合、DIOM は理論的に CG と同等です。もし `k ≤ memory` であれば、`k` は反復回数で、DIOM は理論的に FOM と同等です。それ以外の場合、DIOM は CG と FOM の間を補間し、部分的な再直交化を伴う CG に似ています。

DIOM の利点は、非エルミートまたはエルミート非定義、または非エルミートかつ非定義の線形方程式のシステムをこの単一のアルゴリズムで処理できることです。

#### インターフェース

Krylov メソッド間を簡単に切り替えるには、`method = :diom` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用します。

解の間でメモリを再利用するインプレースバリアントについては、[`diom!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `n` の行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定値を表す長さ `n` のベクトル。

#### キーワード引数

  * `memory`: 新しいベクトルに対して直交化する Krylov 基底の最近のベクトルの数;
  * `M`: 左前処理に使用されるサイズ `n` の非特異行列をモデル化する線形演算子;
  * `N`: 右前処理に使用されるサイズ `n` の非特異行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `reorthogonalization`: 新しいベクトルを Krylov 基底の `memory` 個の最近のベクトルに対して再直交化します;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `2n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ-残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力がログされるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SimpleStats`](@ref) 構造体に収集された実行中の統計。

#### 参考文献

  * Y. Saad, [*Practical use of some krylov subspace methods for solving indefinite and nonsymmetric linear systems*](https://doi.org/10.1137/0905015), SIAM journal on scientific and statistical computing, 5(1), pp. 203–228, 1984.

```
