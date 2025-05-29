```
Near <: IntSelector

Near(x)
```

`x`に最も近いインデックスを選択するセレクタ。

[`Points`](@ref)を使用する場合、これは単に`x`に最も近いインデックス値ですが、[`Intervals`](@ref)を使用する場合、`x`に最も近い区間の*中心*になります。これは`Start`および[`End`](@ref)のロケーションのインデックス値からオフセットされます。

## 例

```jldoctest
using DimensionalData

A = DimArray([1 2 3; 4 5 6], (X(10:10:20), Y(5:7)))
A[X(Near(23)), Y(Near(5.1))]

# output
4
```
