```
KahanSum(T::Type = Float64)
```

全体の合計を追跡します。実質的に精度を倍増させる補償項が含まれています。詳細は[Wikipedia](https://en.wikipedia.org/wiki/Kahan_summation_algorithm)を参照してください。

# 例

```
fit!(KahanSum(Float64), fill(1, 100))
```
