```julia
get_basis(
    AT::Type{<:ExtendableGrids.AssemblyType},
    FEType::Type{<:ExtendableFEMBase.AbstractFiniteElement},
    EG::Type{<:ExtendableGrids.AbstractElementGeometry}
) -> ExtendableFEMBase.var"#closure#123"

```

は、次の形式のクロージャ関数を返します。

```
closure(refbasis, xref)
```

これは、基底関数の評価を参照幾何に対して計算します。
