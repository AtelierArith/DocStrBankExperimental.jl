```
balancedaccuracy(tn::T, fp::T, fn::T, tp::T) where {T<:Integer}
```

感度と特異度の算術平均であり、データが不均衡な場合に使用されます。

# 引数

  * `tn::Integer` 真の陰性
  * `fp::Integer` 偽陽性
  * `fn::Integer` 偽陰性
  * `tp::Integer` 真の陽性
