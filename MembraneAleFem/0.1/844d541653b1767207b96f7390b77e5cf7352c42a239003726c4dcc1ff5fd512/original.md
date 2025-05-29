```
LineGpBasisFns(kv::KnotVector, ngp::Int64)
```

1-D B-spline basis functions and derivatives at all quadrature points on the domain of the [`KnotVector`](@ref) `kv`.

Basis functions are determined at each of the `ngp` Gauss points, over each element. When using B-splines, scenarios often arise where the basis functions are identical across many elements. We accordingly store only the 1-D basis functions over unique elements, as well as a mapping from elements to unique elements. The basis functions at the edges of the 1-D parametric domain are stored separately, as they are required subsequently for application of boundary conditions. The struct has five fields:

  * `nel` –> number of elements in the [`KnotVector`](@ref) `kv`
  * `uel_ids` –> mapping from `elem_id` to `unique_elem_id`
  * `ufns` –> `num_unique_elems`×`ngp` matrix of unique 1-D basis functions, of type [`GpBasisFnsζ`](@ref)
  * `ζmin_fns` –> 1-D basis functions at the min value of the parametric domain
  * `ζmax_fns` –> 1-D basis functions at the max value of the parametric domain

Note that this struct contains no information about how basis functions vary in the orthogonal parametric direction, and thus cannot be directly used to apply boundary conditions. See [`BdryGpBasisFns`](@ref).
