```
fastdensesparsemul_outer_threaded!(C, a, b, α, β)
```

スレッドを使用した、高速な外積で、`C .= β*C + α * a*b'`を計算しますが、Baseよりもはるかに高速です。`Polyester.jl`を使用しています。

  * `a`は密なベクトル（またはビュー）、`b`は疎なベクトル、`C`は密な行列（またはビュー）です。

単一スレッド版については、`fastdensesparsemul_outer!`も参照してください。
