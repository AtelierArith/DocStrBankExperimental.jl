```
Contains <: IntSelector

Contains(x)
```

値が含まれる区間を選択するセレクタです。インデックスに区間が存在しない場合、エラーがスローされます。

[`Intervals`](@ref) または [`Categorical`](@ref) のみで使用できます。

## 例

```jldoctest
using DimensionalData; const DD = DimensionalData
dims_ = X(10:10:20; sampling=DD.Intervals(DD.Center())),
        Y(5:7; sampling=DD.Intervals(DD.Center()))
A = DimArray([1 2 3; 4 5 6], dims_)
A[X(Contains(8)), Y(Contains(6.8))]

# 出力
3
```
