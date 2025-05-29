```
ConstantMean(field, mean_value = 1)
```

スカラー量 $q$ のソース項で、空間的には一定だが、時間的に動的に調整されて $q$ の一定の平均値 $Q$ を維持するためのソース強度。

# 引数

  * `field::Symbol`: 量 $q$ の名前。
  * `mean_value::Real`: 維持される平均値 $Q$。
