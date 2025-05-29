```
CarrMadan(α, bound, dynamics; kwargs...)
```

`quadgk`のオプションの積分設定を持つ`CarrMadan`メソッドを構築します。

# 引数

  * `α`: 減衰係数。
  * `bound`: 積分境界（正の実数）。
  * `dynamics`: 価格のダイナミクス（`marginal_law`をサポートする必要があります）。
  * `kwargs...`: `quadgk`の追加のキーワード引数。
