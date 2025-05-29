```
InterfaceCellValues([::Type{T},] qr::QuadratureRule, func_ip::InterfaceCellInterpolation, [geom_ip::InterfaceCellInterpolation]; use_same_cv=true)
```

An `InterfaceCellValues` is based on two `CellValues`: one for each facet of an `InterfaceCell`. Since one can use the same `CellValues` for both sides, be default the same object is used for better performance. The keyword argument `use_same_cv` can be set to `false` to disable this behavior, if needed.

# Fields

  * `ip::InterfaceCellInterpolation`: interpolation on the interface
  * `here::CellValues`:  values for facet "here"
  * `there::CellValues`:  values for facet "there"
  * `base_indices_here::Vector{Int}`: base function indices on facet "here"
  * `base_indices_there::Vector{Int}`: base function indices on facet "there"
  * `sides_and_baseindices::Tuple`: side and base function for the base `CellValues` for each base function of the `InterfaceCellValues`
