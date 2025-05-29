```
Contains <: IntSelector

Contains(x)
Contains(a, b)
```

値が含まれている区間を選択するセレクタです。区間がルックアップに存在しない場合、エラーがスローされます。

[`Intervals`](@ref) または [`Categorical`](@ref) のみで使用できます。[`Categorical`](@ref) の場合は、[`At`](@ref) を使用することにフォールバックします。`Contains` は `Base.contains` と混同しないでください - 文字列のようなカテゴリカル値に値が含まれているかを確認するには `Where(contains(x))` を使用してください。

`x` は単一のインデックスを選択するための任意の値、またはインデックスのベクトルを選択するための値の `Vector` です。2つの値 `a` と `b` が使用される場合、それらの間の範囲が選択されます。

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
