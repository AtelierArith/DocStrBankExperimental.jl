```
mcc(tn::T, fp::T, fn::T, tp::T) where {T<:Integer}
```

マシューズ相関係数、クラスの不均衡問題を克服するために使用されるファイ係数の特別なケースのパフォーマンス指標

# 引数

  * `tn::Integer` 真の陰性
  * `fp::Integer` 偽陽性
  * `fn::Integer` 偽陰性
  * `tp::Integer` 真の陽性

# 参考文献

1.Chicco, D., Jurman, G. マシューズ相関係数（MCC）が二項分類評価におけるF1スコアおよび精度に対して持つ利点。BMC Genomics 21, 6 (2020).
