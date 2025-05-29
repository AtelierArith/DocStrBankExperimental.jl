```
NEWMA(λ::Float64, g::F, dat::FunctionalData)
```

関数回帰モデルの標準誤差を計算することによって、NEWMA管理図を構築します。

# 引数

  * `λ::Float64`: EWMAスムージング定数。0と1の間でなければなりません。
  * `g::F`: 推定された回帰関数オブジェクト。`predict(g::F, x::AbstractVector)`というシグネチャのメソッドを持っている必要があります。
  * `dat::FunctionalData`: 回帰曲線の観測値を含む`FunctionalData`オブジェクト。
  * `Ej::Vector{Float64}`: 現在のスムージングされた観測値。

# 戻り値

構築されたNEWMA管理図。

# 例

```
using Loess
xs = 10 .* rand(100)
ys = sin.(xs) .+ rand(100)
g = loess(xs, ys)
dat = FunctionalData(xs, ys)
NEWMA(0.2, g, dat)
```
