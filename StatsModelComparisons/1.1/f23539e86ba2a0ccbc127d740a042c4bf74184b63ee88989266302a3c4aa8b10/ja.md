```
gpdfitnew(x)
```

一般化パレート分布 (GPD) のパラメータを推定します。データに基づいて二項パラメータ一般化パレート分布のパラメータの経験的ベイズ推定を返します。

# 引数

  * `x::AbstractArray`: 一次元データ配列。

# 戻り値

  * `k::Float64, sigma::Float64`: 推定されたパラメータ値。

# 注意事項

  * この関数は、より一般的なパラメータ化であるため、Zhang と Stephens の k の負の値を返します。
