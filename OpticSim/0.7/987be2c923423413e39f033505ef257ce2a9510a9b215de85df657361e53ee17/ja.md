レイ上の非重複区間の順序付けられた系列を表すデータ型。任意の`Interval`の配列をコンストラクタに入力することができ、それらは自動的に有効な`DisjointUnion`（または適切であれば単一の[`Interval`](@ref)）に処理されます。

```julia
DisjointUnion(intervals::AbstractVector{Interval{R}})
```
