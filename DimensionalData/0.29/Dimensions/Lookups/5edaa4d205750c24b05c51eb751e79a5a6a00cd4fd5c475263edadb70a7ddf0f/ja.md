```
All <: Selector

All(selectors::Selector...)
```

他のセレクタの結果を組み合わせるセレクタです。使用されるインデックスは、すべての結果の和集合で、昇順にソートされます。

## 例

```jldoctest
using DimensionalData, Unitful

dimz = X(10.0:20:200.0), Ti(1u"s":5u"s":100u"s")
A = DimArray((1:10) * (1:20)', dimz)
A[X=All(At(10.0), At(50.0)), Ti=All(1u"s"..10u"s", 90u"s"..100u"s")]

# 出力

┌ 2×4 DimArray{Int64, 2} ┐
├────────────────────────┴─────────────────────────────────────────────── dims ┐
  ↓ X  Sampled{Float64} [10.0, 50.0] ForwardOrdered Irregular Points,
  → Ti Sampled{Unitful.Quantity{Int64, 𝐓, Unitful.FreeUnits{(s,), 𝐓, nothing}}} [1 s, 6 s, 91 s, 96 s] ForwardOrdered Irregular Points
└──────────────────────────────────────────────────────────────────────────────┘
  ↓ →  1 s  6 s  91 s  96 s
 10.0  1    2    19    20
 50.0  3    6    57    60
```
