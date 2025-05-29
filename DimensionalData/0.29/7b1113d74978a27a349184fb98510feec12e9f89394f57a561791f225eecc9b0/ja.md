```
reorder(A::Union{AbstractDimArray,AbstractDimStack}, order::Pair...)
reorder(A::Union{AbstractDimArray,AbstractDimStack}, order)
reorder(A::Dimension, order::Order)
```

すべての次元インデックス/配列を `order` に再配置するか、指定された次元のインデックスを `order` で再配置します。

`order` は [`Order`](@ref) または `Dimension => Order` ペアであることができます。次元のタプルまたは `dims` を定義する任意のオブジェクトを使用することができ、その場合はこのオブジェクトの次元が再配置に使用されます。

軸の反転が必要ない場合、同じオブジェクトが割り当てなしで返されます。

## 例

```jldoctest
using DimensionalData

# DimArrayを作成
da = DimArray([1 2 3; 4 5 6], (X(10:10:20), Y(300:-100:100)))

# それを反転させる
rev = reverse(da, dims=Y)

# reorderで`da`を使用すると元の順序に戻ります
reorder(rev, da) == da

# 出力
true
```
