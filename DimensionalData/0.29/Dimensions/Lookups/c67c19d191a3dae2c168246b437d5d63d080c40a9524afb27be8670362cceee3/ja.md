```
Between <: ArraySelector

Between(a, b)
```

非推奨: `Between(a, b)`の代わりに`a..b`を使用してください。`OpenInterval(a, b)`のような`IntervalSets.jl`の他の`Interval`オブジェクトも機能し、正しい開閉境界を提供します。

`Between`は、`DataFrames.Between`との衝突を避けるために将来削除されます。

2つの値の間に位置するすべてのインデックスを取得するセレクタで、下限値には`>=`、上限値には`<`が評価されます。これは、隣接する2つの`Between`選択で同じ値が2回カウントされないことを意味します。

[`Intervals`](@ref)の場合、全体の区間は値の間に存在しなければなりません。[`Points`](@ref)の場合、ポイントは値の間に落ちる必要があります。異なる[`Sampling`](@ref)タイプは、同じ入力で異なる結果を返す場合があります - これは意図された動作です。

[`Irregular`](@ref)区間の`Between`は少し複雑です。区間は、値と次の（`Start`ローカスの場合）または前の（[`End`](@ref)ローカスの場合）値との距離です。

[`Center`](@ref)の場合、2つのインデックス値の間の中点を各区間の開始と終了とします。これは、インデックス内の値に対して意味を持つ場合もあれば、持たない場合もあるため、注意して`Irregular` `Intervals(Center())`とともに`Between`を使用してください。

## 例

```jldoctest
using DimensionalData

A = DimArray([1 2 3; 4 5 6], (X(10:10:20), Y(5:7)))
A[X(Between(15, 25)), Y(Between(4, 6.5))]

# 出力

┌ 1×2 DimArray{Int64, 2} ┐
├────────────────────────┴───────────────────────────── dims ┐
  ↓ X Sampled{Int64} 20:10:20 ForwardOrdered Regular Points,
  → Y Sampled{Int64} 5:6 ForwardOrdered Regular Points
└────────────────────────────────────────────────────────────┘
  ↓ →  5  6
 20    4  5
```
