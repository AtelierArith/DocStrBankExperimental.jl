```
BagNode{T <: Union{AbstractMillNode, Missing}, B <: AbstractBags, C} <: AbstractBagNode
```

マルチインスタンス学習問題を表すデータノード。

タイプ `T` のサブツリーに格納されたインスタンス、タイプ `B` のバッグインデックス、およびオプションのメタデータタイプ `C` を含みます。

参照: [`WeightedBagNode`](@ref), [`AbstractBagNode`](@ref),     [`AbstractMillNode`](@ref), [`BagModel`](@ref).
