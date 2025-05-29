```
struct TProductFESpace{S} <: SingleFieldFESpace
  space::S
  spaces_1d::Vector{<:SingleFieldFESpace}
  trian::TProductTriangulation
end
```

Tensor product single field `FESpace`, storing a vector of 1-D `FESpace`s `spaces_1d` of length D, and the D-dimensional `FESpace` `space` defined as their tensor product. The tensor product triangulation `trian` is provided as a field to avoid incompatibility issues when passing to `MultiField` scenarios
