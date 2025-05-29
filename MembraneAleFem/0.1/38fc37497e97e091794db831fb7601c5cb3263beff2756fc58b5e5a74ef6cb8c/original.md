```
BdryGpBasisFns(line_gp_fns::LineGpBasisFns, perp_edge_fns::GpBasisFnsζ, bdry::Boundary)
```

2-D B-spline basis functions and derivatives at all quadrature points on a boundary.

The [`LineGpBasisFns`](@ref) struct `line_gp_fns` contains all 1-D basis functions and derivatives along the boundary, with `ngp` Gauss points for each element. Here `perp_edge_fns` are the basis functions and derivatives at the boundary in the orthogonal parametric direction, as contained in a [`GpBasisFnsζ`](@ref) struct. For example, on the `RIGHT` boundary, `line_gp_fns` captures 1-D derivatives in the $ζ^2$ direction, while `perp_edge_fns` contains 1-D derivatives in the $ζ^1$ direction on the right edge. With knowledge of the underlying tensor product structure [piegl-tiller](@citep), the 2-D basis functions along the specified [`Boundary`](@ref) `bdry` are generated. The struct has four fields:

  * `nel` –> number of elements associated with [`LineGpBasisFns`](@ref) `line_gp_fns`
  * `uel_ids` –> mapping from `elem_id` to `unique_elem_id`
  * `ufns` –> `num_unique_elems`×`ngp` matrix of unique 2-D basis functions, of type [`GpBasisFnsζα`](@ref)
  * `bdry` –> [`Boundary`](@ref) of the parametric domain
