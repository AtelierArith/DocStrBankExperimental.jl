```julia
RGB_refine(
    source_grid::ExtendableGrids.ExtendableGrid{T, K},
    facemarkers::Vector{Bool};
    store_parents
) -> ExtendableGrids.ExtendableGrid

```

三角形メッシュの赤-緑-青メッシュ細分化によって新しいExtendableGridを生成します。詳細は以下を参照してください。

Carstensen, C. –An Adaptive Mesh-Refining Algorithm Allowing for an H^1 Stable L^2 Projection onto Courant Finite Element Spaces– Constr Approx 20, 549–564 (2004). https://doi.org/10.1007/s00365-003-0550-5

bool配列facemarkersは、どの面を二分すべきかを決定します。マークされた面を持つ各三角形の最初の面も細分化されるように、クローズ処理が行われることに注意してください。
