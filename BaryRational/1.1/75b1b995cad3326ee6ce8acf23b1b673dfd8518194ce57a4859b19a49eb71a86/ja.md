```
bary(z, f, x, w)
```

f(z)を評価します

# 引数

  * z::Z                 : fを評価する点
  * f::AbstractVector{F} : xにおける関数値のベクトル
  * x::AbstractVector{X} : fの評価位置のベクトル（ソート済み）
  * w::AbstractVector{W} : 位置xの重み
