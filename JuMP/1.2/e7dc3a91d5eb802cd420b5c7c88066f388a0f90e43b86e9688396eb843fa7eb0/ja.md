```
optimizer_index(cr::ConstraintRef{Model})::MOI.ConstraintIndex
```

`cr`に対応する制約のインデックスを最適化モデルから返します。最適化プログラムが設定されていない場合は[`NoOptimizer`](@ref)をスローし、最適化プログラムが設定されているが接続されていない場合や制約がブリッジされている場合は`ErrorException`をスローします。
