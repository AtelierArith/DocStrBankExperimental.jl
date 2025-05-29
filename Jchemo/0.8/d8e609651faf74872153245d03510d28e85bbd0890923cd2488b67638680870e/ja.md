```
sampcla(x, k::Union{Int, Vector{Int}}, y = nothing)
```

層化サンプリングによるトレーニングセットとテストセットの構築。

  * `x` : 観測のクラスメンバーシップ (n)。
  * `k` : 各クラスからサンプリングするテスト観測の数。`k` が単一の値の場合、サンプリングされる観測の数は各クラスで同じになります。あるいは、`k` は `x` のクラス数と等しい長さのベクトルであることもできます。
  * `y` : 系統的サンプリングに使用される定量変数 (n)。

2つの出力が返されます (= データの行インデックス):

  * `train` (n - `k`),
  * `test` (`k`)。

`y` が `nothing` の場合、サンプリングはランダムですが、そうでない場合はソートされた `y` に対して系統的になります（関数 `sampsys` を参照）。

## 参考文献

Naes, T., 1987. The design of calibration in near infra-red reflectance analysis by clustering. Journal of Chemometrics 1, 121-134.

## 例

```julia
using Jchemo
x = string.(repeat(1:3, 5))
n = length(x)
tab(x)
k = 2 
res = sampcla(x, k)
res.test
x[res.test]
tab(x[res.test])

y = rand(n)
res = sampcla(x, k, y)
res.test
x[res.test]
tab(x[res.test])
```
