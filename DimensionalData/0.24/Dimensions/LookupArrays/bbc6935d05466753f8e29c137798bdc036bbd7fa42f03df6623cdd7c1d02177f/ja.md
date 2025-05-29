```
Touches <: ArraySelector

Touches(a, b)
```

閉区間2値に接触するすべてのインデックスを取得するセレクタで、供給された範囲と相互作用する可能性のある最大の面積を対象とします。

これは、例えばラスタライズするためにエリアをサブセットする際に、エリアに接触するピクセルを含めたい場合があるため、`..` よりも優れています。

Touchesは、ルックアップに区間が含まれている場合に閉区間を使用するのとは異なります - もし区間のいずれかが接触していれば、それらは含まれます。`..`を使用すると、全体のセル区間がセレクタ区間内に収まらない限り、破棄されます。

## 例

```jldoctest
using DimensionalData

A = DimArray([1 2 3; 4 5 6], (X(10:10:20), Y(5:7)))
A[X(Touches(15, 25)), Y(Touches(4, 6.5))]

# 出力
1×2 DimArray{Int64,2} with dimensions:
  X Sampled{Int64} 20:10:20 ForwardOrdered Regular Points,
  Y Sampled{Int64} 5:6 ForwardOrdered Regular Points
     5  6
 20  4  5
```
