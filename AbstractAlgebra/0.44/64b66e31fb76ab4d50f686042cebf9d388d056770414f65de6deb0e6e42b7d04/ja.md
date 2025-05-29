```
compose(f::RelPowerSeriesRingElem, g::RelPowerSeriesRingElem; inner)
```

系列 $a$ を系列 $b$ と合成し、結果を返します。

  * `inner = :second` の場合、`f(g)` が返され、`g` は正の評価を持つ必要があります。
  * `inner = :first` の場合、`g(f)` が返され、`f` は正の評価を持つ必要があります。
