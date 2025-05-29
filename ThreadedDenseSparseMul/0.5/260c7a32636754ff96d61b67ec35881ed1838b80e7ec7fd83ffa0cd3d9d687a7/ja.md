```
fastdensesparsemul_outer!(C, a, b, α, β)
```

`C .= β*C + α * a*b'` を計算する際の高速外積ですが、Baseよりもはるかに速いです。

  * `a` は密なベクトル（またはビュー）、`b` は疎なベクトル、`C` は密な行列（またはビュー）です。

また、`Polyester.jl` を使用したマルチスレッド版の `fastdensesparsemul_outer_threaded!` も参照してください。
