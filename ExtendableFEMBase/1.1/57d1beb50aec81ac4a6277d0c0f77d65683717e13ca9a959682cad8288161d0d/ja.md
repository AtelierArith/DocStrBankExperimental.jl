```julia
VertexRule(
    ET::Type{ExtendableGrids.Edge1D};
    ...
) -> ExtendableFEMBase.SQuadratureRule{Float64, ExtendableGrids.Edge1D, 1}
VertexRule(
    ET::Type{ExtendableGrids.Edge1D},
    order;
    T
) -> ExtendableFEMBase.SQuadratureRule{Float64, ExtendableGrids.Edge1D, 1}

```

は、要素の幾何学の頂点で評価される数値積分ルールを設定します。数値積分の観点からは最適ではありませんが、補間時に役立ちます。xrefの順序はH1Pk要素のdof順序と一致することに注意してください。
