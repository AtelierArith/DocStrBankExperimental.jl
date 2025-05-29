```
compose!(m, m2, m1) -> m
```

`TPS`（または `TPS` マップ）`m2 ∘ m1` を合成し、結果を `m` に設定します。GTPSA に変数またはパラメータが 1 つ以上ある場合、`m1` は変数とパラメータの総数に等しい長さの配列でなければなりません。

# 引数

  * `m::Union{AbstractArray{TPS{T,D}},TPS{T,D}}`
  * `m2::Union{AbstractArray{TPS{T,D2}},TPS{T,D2}}`
  * `m1::Union{AbstractArray{TPS{T,D1}},TPS{T,D1}}`
