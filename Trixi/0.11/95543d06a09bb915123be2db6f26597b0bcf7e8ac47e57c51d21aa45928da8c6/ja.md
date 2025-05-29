```
DGMultiMesh(dg::DGMulti{NDIMS}, cells_per_dimension, mapping;
            is_on_boundary=nothing,
            periodicity=ntuple(_ -> false, NDIMS), kwargs...) where {NDIMS}
```

`dg.basis.element_type`を持つ`Curved()` [`DGMultiMesh`](@ref)を構築します。

  * `mapping`は、参照[-1, 1]^NDIMSドメインからマッピングされたドメインへの関数です。例えば、2Dでは`xy = mapping(x, y)`です。
  * `is_on_boundary`は、`Dict{Symbol, <:Function}`を使用して境界を指定します。
  * `periodicity`は、(x,y,z)方向の周期性を指定する`Bool`のタプルです。
