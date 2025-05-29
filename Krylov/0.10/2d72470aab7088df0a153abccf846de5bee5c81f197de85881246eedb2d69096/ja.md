```
(x, stats) = symmlq(A, b::AbstractVector{FC};
                    M=I, ldiv::Bool=false, window::Int=5,
                    transfer_to_cg::Bool=true, λ::T=zero(T),
                    λest::T=zero(T), etol::T=√eps(T),
                    conlim::T=1/√eps(T), atol::T=√eps(T),
                    rtol::T=√eps(T), itmax::Int=0,
                    timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                    callback=workspace->false, iostream::IO=kstdout)
```

`T` は `Float32`、`Float64` または `BigFloat` のような `AbstractFloat` です。`FC` は `T` または `Complex{T}` です。

```
(x, stats) = symmlq(A, b, x0::AbstractVector; kwargs...)
```

SYMMLQ は初期推定値 `x0` からウォームスタートすることができ、`kwargs` は上記と同じキーワード引数です。

シフトされた線形システムを解く

```
(A + λI) x = b
```

サイズ n の SYMMLQ メソッドを使用して、ここで λ はシフトパラメータであり、A はエルミート行列です。

SYMMLQ は単調な誤差 ‖x* - x‖₂ を生成します。

#### インターフェース

Krylov メソッド間で簡単に切り替えるには、`method = :symmlq` を使用して一般的なインターフェース [`krylov_solve`](@ref) を使用してください。

メモリを再利用するインプレースバリアントについては、[`symmlq!`](@ref) を参照してください。

#### 入力引数

  * `A`: 次元 `n` のエルミート行列をモデル化する線形演算子;
  * `b`: 長さ `n` のベクトル。

#### オプション引数

  * `x0`: 解 `x` の初期推定値を表す長さ `n` のベクトル。

#### キーワード引数

  * `M`: 中心前処理に使用されるサイズ `n` のエルミート正定値行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が `ldiv!` または `mul!` を使用するかどうかを定義します;
  * `window`: 誤差の下限を蓄積するために使用される反復回数;
  * `transfer_to_cg`: SYMMLQ ポイントから CG ポイントへの転送、存在する場合。転送は残差ノルムに基づいています;
  * `λ`: 正則化パラメータ;
  * `λest`: 正定値システムを解くときの最小固有値 `λₘᵢₙ` に対する正の厳密下限、例えば `λest = (1-10⁻⁷)λₘᵢₙ`;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `etol`: 誤差の下限に基づく停止許容誤差;
  * `conlim`: 解が放棄される条件数の推定値の限界;
  * `itmax`: 最大反復回数。`itmax=0` の場合、デフォルトの反復回数は `2n` に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は `verbose` 回の反復ごとに表示されます;
  * `history`: 残差ノルムや Aᴴ 残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)` として呼び出される関数またはファンクタで、Krylov メソッドを終了すべき場合は `true` を返し、そうでない場合は `false` を返します;
  * `iostream`: 出力が記録されるストリーム。

#### 出力引数

  * `x`: 長さ `n` の密なベクトル;
  * `stats`: [`SymmlqStats`](@ref) 構造体に収集された実行中の統計。

#### 参考文献

  * C. C. Paige と M. A. Saunders, [*Solution of Sparse Indefinite Systems of Linear Equations*](https://doi.org/10.1137/0712047), SIAM Journal on Numerical Analysis, 12(4), pp. 617–629, 1975.
