```
optimize_offsets!(g::BVHGraph)
```

各エッジについて、そのソースとデスティネーションの間のグローバル位置の平均ノルムを計算し、それに応じてオフセットベクトルを調整します。

この関数は、頂点を削除した後に、元のグローバル位置からの頂点の偏差を減少させることができます。なぜなら、新しいオフセットは通常バイアスがかかっているからです。

# 例

```julia
julia> g = load("Test.bvh") |>
           global_positions! |>
           remove_joint!(7) |>
           remove_joint!(13) |>
           remove_joints!("J_L_Bale", "J_R_Bale", "J_L4", "J_L3", "J_L1", "J_T12", "J_T10", "J_T9", "J_T8", "J_T6", "J_T5", "J_T4", "J_T3", "J_T2") |>
           optimize_offsets!
BVHGraph
Name: Test.bvh
[...]
```

参照: [`total_squared_errors`](@ref)
