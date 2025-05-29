```
NSGA3(;
    N = 100,
    η_cr = 20,
    p_cr = 0.9,
    η_m = 20,
    p_m = 1.0 / D,
    partitions = 12,
    reference_points = Vector{Float64}[],
    information = Information(),
    options = Options(),
)

メタヒューリスティックNSGA-IIIのパラメータ。

パラメータ:

  * `N` 集団のサイズ。
  * `η_cr`  交差のためのη。
  * `p_cr`  交差確率。
  * `η_m`  突然変異オペレーターのためのη。
  * `p_m` 突然変異確率（デフォルトでD次元問題のための1/D）。
  * `reference_points` 通常`gen_ref_dirs`によって生成される参照点。
  * `partitions` `reference_points`が空の場合のDasとDennisの参照点の数。

NSGA3を使用するには、目的関数からの出力は3つ組 `(f::Vector, g::Vector, h::Vector)` である必要があります。ここで、`f`は目的関数を含み、`g`と`h`はそれぞれ不等式および等式制約です。

実行可能な解は `g_i(x) ≤ 0` および `h_j(x) = 0` である必要があります。

```

julia using Metaheuristics

# 目的関数、境界、および真のパレートフロント

f, bounds, pf = Metaheuristics.TestProblems.get_problem(:DTLZ2)

# パラメータを定義する（デフォルトのパラメータを使用するには`NSGA3()`を使用）

nsga3 = NSGA3(p_cr = 0.9)

# 最適化

status = optimize(f, bounds, nsga3)

# 結果を表示

display(status) ```
