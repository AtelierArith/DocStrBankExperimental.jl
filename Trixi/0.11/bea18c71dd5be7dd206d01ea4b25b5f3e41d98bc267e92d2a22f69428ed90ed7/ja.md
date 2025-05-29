```
DGMultiMesh(dg::DGMulti, cells_per_dimension;
            coordinates_min=(-1.0, -1.0), coordinates_max=(1.0, 1.0),
            is_on_boundary=nothing,
            periodicity=ntuple(_ -> false, NDIMS))
```

Cartesian [`DGMultiMesh`](@ref) を要素タイプ `dg.basis.element_type` で構築します。ドメインは区間 `[coordinates_min[i], coordinates_max[i]]` のテンソル積です。

  * `is_on_boundary` は `Dict{Symbol, <:Function}` を使用して境界を指定します。
  * `periodicity` は (x,y,z) 方向の周期性を指定する `Bool` のタプルで、`true`/`false` です。
