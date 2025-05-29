```julia
get_polynomialorder(
    AT::Type{<:ExtendableGrids.AssemblyType},
    FE::Type{<:ExtendableFEMBase.AbstractFiniteElement},
    EG::Type{<:ExtendableGrids.AbstractElementGeometry}
) -> Int64

```

は、基底関数の期待される多項式次数を返します（デフォルトの数値積分次数を決定するために使用されます）。
