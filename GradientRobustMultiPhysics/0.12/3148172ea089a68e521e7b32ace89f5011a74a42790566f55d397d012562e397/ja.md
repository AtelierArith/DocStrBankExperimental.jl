```julia
add_boundarydata!(
    PDE::GradientRobustMultiPhysics.PDEDescription,
    position::Int64,
    regions,
    btype::Type{<:GradientRobustMultiPhysics.AbstractBoundaryType};
    data,
    mask
) -> Vector{GradientRobustMultiPhysics.BoundaryData}

```

指定された位置に指定されたAbstractBoundaryTypeで与えられた境界データをPDEDescriptionのBoundaryOperatorに追加します。

注意: データ関数が時間依存である場合（ユーザーデータのドキュメントを参照）、それはTimeControlSolverの任意のadvance!ステップで評価されます。
