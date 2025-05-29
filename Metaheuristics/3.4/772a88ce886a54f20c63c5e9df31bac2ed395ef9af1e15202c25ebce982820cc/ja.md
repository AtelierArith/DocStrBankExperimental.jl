```
CGSA(;
    N::Int    = 30,
    chValueInitial::Real   = 20,
    chaosIndex::Real   = 9,
    ElitistCheck::Int    = 1,
    Rpower::Int    = 1,
    Rnorm::Int    = 2,
    wMax::Real   = chValueInitial,
    wMin::Real   = 1e-10,
    information = Information(),
    options = Options()
)

CGSAは、重力探索アルゴリズムのためのカオス重力定数を持つGSAアルゴリズムの拡張です。

参考文献: 重力探索アルゴリズムのためのカオス重力定数. Applied Soft Computing 53 (2017): 407-419.

パラメータ:

  * N: 集団サイズ
  * chValueInitial: カオス値の初期値
  * chaosIndex: 整数 1 ≤ chaosIndex ≤ 10 はカオスをモデル化する関数
  * Rpower: 距離ノルム(x)^Rpowerに関連するべき乗
  * Rnorm: norm(x, Rnorm)の値

# 例

```

jldoctest julia> f(x) = sum(x.^2) f (generic function with 1 method)

julia> optimize(f, [-1 -1 -1; 1 1 1.0], CGSA()) +=========== RESULT ==========+   iteration: 500     minimum: 8.63808e-08   minimizer: [0.0002658098418993323, -1.140808975532608e-5, -0.00012488307670533095]     f calls: 15000  total time: 0.1556 s +============================+

julia> optimize(f, [-1 -1 -1; 1 1 1.0], CGSA(N = 80, chaosIndex = 1)) +=========== RESULT ==========+   iteration: 500     minimum: 1.0153e-09   minimizer: [-8.8507563788141e-6, -1.3050111801923072e-5, 2.7688577445980026e-5]     f calls: 40000  total time: 1.0323 s +============================+ ```
