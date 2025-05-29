```julia
struct NonAllocatedFunctionSpace{NDof, Map, Conn<:(FiniteElementContainers.ElementField), DofConn<:(FiniteElementContainers.ElementField), RefFE<:ReferenceFiniteElements.ReferenceFE} <: FiniteElementContainers.FunctionSpace{NDof, Conn<:(FiniteElementContainers.ElementField), RefFE<:ReferenceFiniteElements.ReferenceFE}
```

  * `elem_id_map::Any`
  * `conn::FiniteElementContainers.ElementField`
  * `dof_conn::FiniteElementContainers.ElementField`
  * `ref_fe::ReferenceFiniteElements.ReferenceFE`
