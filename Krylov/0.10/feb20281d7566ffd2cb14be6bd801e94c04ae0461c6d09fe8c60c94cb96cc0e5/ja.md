```
(x, stats) = minres(A, b::AbstractVector{FC};
                    M=I, ldiv::Bool=false, window::Int=5,
                    linesearch::Bool=false, λ::T=zero(T), atol::T=√eps(T),
                    rtol::T=√eps(T), etol::T=√eps(T),
                    conlim::T=1/√eps(T), itmax::Int=0,
                    timemax::Float64=Inf, verbose::Int=0, history::Bool=false,
                    callback=workspace->false, iostream::IO=kstdout)
```

`T`は`Float32`、`Float64`、または`BigFloat`などの`AbstractFloat`です。`FC`は`T`または`Complex{T}`です。

```
(x, stats) = minres(A, b, x0::AbstractVector; kwargs...)
```

MINRESは、初期推定値`x0`からウォームスタートできます。`kwargs`は上記と同じキーワード引数です。

シフトされた線形最小二乗問題を解く

```
minimize ‖b - (A + λI)x‖₂²
```

またはシフトされた線形システム

```
(A + λI) x = b
```

サイズnの問題をMINRES法を使用して解きます。ここで、λ ≥ 0はシフトパラメータで、Aはエルミート行列です。

MINRESは、Aが正定値であるときにAx=bにCRを適用することと形式的に同等ですが、通常はより安定しており、Aが不定の場合にも適用されます。

MINRESは単調な残差‖r‖₂と最適性残差‖Aᴴr‖₂を生成します。

#### インターフェース

Krylov法の間で簡単に切り替えるには、`method = :minres`を使用して一般的なインターフェース[`krylov_solve`](@ref)を使用します。

解の間でメモリを再利用するインプレースバリアントについては、[`minres!`](@ref)を参照してください。

#### 入力引数

  * `A`: 次元`n`のエルミート行列をモデル化する線形演算子;
  * `b`: 長さ`n`のベクトル。

#### オプション引数

  * `x0`: 解`x`の初期推定値を表す長さ`n`のベクトル。

#### キーワード引数

  * `M`: 中心前処理に使用されるサイズ`n`のエルミート正定値行列をモデル化する線形演算子;
  * `ldiv`: 前処理器が`ldiv!`または`mul!`を使用するかどうかを定義します;
  * `window`: 誤差の下限を蓄積するために使用される反復回数;
  * `linesearch`: `true`の場合、解がラインサーチを伴う不正確なニュートン法で使用されることを示します。`linesearch`がtrueで非正の曲率が検出されると、解は反復に依存します: 反復k = 1では、右辺は`workspace.npc_dir`を前処理された初期残差として返されます; 反復k > 1では、反復k-1からの解が`workspace.npc_dir`を最新の残差として返されます。（MINRESソルバーは反復1から開始するため、最初の反復はk = 1です）;
  * `λ`: 正則化パラメータ;
  * `atol`: 残差ノルムに基づく絶対停止許容誤差;
  * `rtol`: 残差ノルムに基づく相対停止許容誤差;
  * `etol`: 誤差の下限に基づく停止許容誤差;
  * `conlim`: 解が放棄される条件数の推定値の制限;
  * `itmax`: 最大反復回数。`itmax=0`の場合、デフォルトの反復回数は`2n`に設定されます;
  * `timemax`: 秒単位の時間制限;
  * `verbose`: 詳細モードが有効な場合（verbose > 0）、追加の詳細が表示されます。情報は`verbose`反復ごとに表示されます;
  * `history`: 残差ノルムやAᴴ残差ノルムなど、実行中の追加統計を収集します;
  * `callback`: `callback(workspace)`として呼び出される関数またはファンクタで、Krylov法を終了すべき場合は`true`を返し、そうでない場合は`false`を返します;
  * `iostream`: 出力が記録されるストリーム。

#### 出力引数

  * `x`: 長さ`n`の密なベクトル;
  * `stats`: [`SimpleStats`](@ref)構造体に収集された実行中の統計。

#### 参考文献

  * C. C. PaigeとM. A. Saunders、[*Solution of Sparse Indefinite Systems of Linear Equations*](https://doi.org/10.1137/0712047)、SIAM Journal on Numerical Analysis、12(4)、pp. 617–629、1975年。
  * Y. LiuとF. Roosta、[*MINRES: From Negative Curvature Detection to Monotonicity Properties*](https://doi.org/10.1137/21M143666X)、SIAM Journal on Optimization、32(4)、pp. 2636–2661、2022年。
