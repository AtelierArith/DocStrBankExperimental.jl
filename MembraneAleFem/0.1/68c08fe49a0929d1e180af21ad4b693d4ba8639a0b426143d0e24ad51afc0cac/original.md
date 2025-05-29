```
AreaGpBasisFns(line_gp_fns1::LineGpBasisFns, line_gp_fns2::LineGpBasisFns)
```

2-D B-spline basis functions and derivatives at all quadrature points in the mesh area.

The two [`LineGpBasisFns`](@ref) structs passed in, `line_gp_fns1` and `line_gp_fns2`, respectively contain 1-D derivatives in the $ζ^1$ and $ζ^2$ directions. With the tensor product structure of B-splines over a surface [piegl-tiller](@citep), it is straightforward to calculate the 2-D basis functions and their derivatives. As is the case for [`LineGpBasisFns`](@ref), a mapping from elements to unique elements is generated; only unique basis function calculations are stored. This struct has three fields:

  * `nel` –> number of area elements
  * `uel_ids` –> mapping from `elem_id` to `unique_elem_id`
  * `ufns` –> `num_unique_elems`×`ngp` matrix of unique 2-D basis functions, of type [`GpBasisFnsζα`](@ref)
