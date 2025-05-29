```
find_equilibria(
    payoff_functions::Tuple{Function, Function, Function},
    params::NamedTuple;
    num_initial_guesses::Int = 1000,
    solver_tol::Float64 = 1e-8,
    equilibrium_tol::Float64 = 1e-5,
    validity_tol::Float64 = 1e-6,
    stability_tol::Float64 = 1e-6
) -> Tuple{Vector{Vector{Float64}}, Vector{Bool}}
```

レプリケーターダイナミクスシステムの均衡を見つけるために、戦略の頻度が変化しなくなる点を数値的に解決します。

# 引数

  * `payoff_functions`: 各戦略に対応する3つのペイオフ関数のタプル。
  * `params`: ペイオフ関数のための追加パラメータ（オプション）。
  * `num_initial_guesses`: 均衡を見つけるために使用する初期推測の数。
  * `solver_tol`: 数値ソルバーの許容誤差。
  * `equilibrium_tol`: 均衡を一意と見なすための許容誤差。
  * `validity_tol`: シンプレックス内で均衡を検証するための許容誤差。
  * `stability_tol`: 安定性分析のための許容誤差。

# 戻り値

  * 次の内容を含むタプル：

      * `equilibria`: 均衡を表す戦略の頻度のベクトル。
      * `stability_status`: 各均衡が安定かどうかを示すブール値のベクトル。

# 注意事項

  * レプリケータ方程式の根を見つけるために `nlsolve` を使用します。
  * シンプレックスの外にある均衡や重複する均衡は除外されます。
