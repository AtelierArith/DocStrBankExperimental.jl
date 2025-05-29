```
SPEA2(;
    N = 100,
    η_cr = 20,
    p_cr = 0.9,
    η_m = 20,
    p_m = 1.0 / D,
    information = Information(),
    options = Options(),
)

メタヒューリスティックNSGA-IIのパラメータ。

パラメータ:

  * `N` 集団のサイズ。
  * `η_cr` 交差のためのη。
  * `p_cr` 交差確率。
  * `η_m` 突然変異オペレーターのためのη。
  * `p_m` 突然変異確率（デフォルトでD次元問題のための1/D）。

SPEA2を使用するには、目的関数の出力は3つ組 `(f::Vector, g::Vector, h::Vector)` である必要があります。ここで、`f` は目的関数を含み、`g` と `h` はそれぞれ不等式制約と等式制約です。

実行可能な解は `g_i(x) ≤ 0` および `h_j(x) = 0` である必要があります。

```

julia using Metaheuristics

# 次元

D = 2

# 目的関数

f(x) = ( x, [sum(x.^2) - 1], [0.0] ) 

# 範囲

bounds = [-1 -1;            1  1.0         ]

# パラメータを定義する（デフォルトのパラメータを使用するには `SPEA2()` を使用）

nsga2 = SPEA2(N = 100, p_cr = 0.85)

# 最適化

status = optimize(f, bounds, nsga2)

# 結果を表示

display(status) ```
