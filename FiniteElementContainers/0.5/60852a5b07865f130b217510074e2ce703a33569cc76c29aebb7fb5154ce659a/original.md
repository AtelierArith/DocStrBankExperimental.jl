```julia
struct VectorizedPreAllocatedFunctionSpace{NDof, Map, Conn<:(FiniteElementContainers.ElementField), DofConn<:(FiniteElementContainers.ElementField), RefFE<:ReferenceFiniteElements.ReferenceFE, V1<:FiniteElementContainers.QuadratureField, V2<:FiniteElementContainers.QuadratureField, V3<:FiniteElementContainers.QuadratureField} <: FiniteElementContainers.FunctionSpace{NDof, Conn<:(FiniteElementContainers.ElementField), RefFE<:ReferenceFiniteElements.ReferenceFE}
```

  * `elem_id_map::Any`
  * `conn::FiniteElementContainers.ElementField`
  * `dof_conn::FiniteElementContainers.ElementField`
  * `ref_fe::ReferenceFiniteElements.ReferenceFE`
  * `Ns::FiniteElementContainers.QuadratureField`
  * `∇N_Xs::FiniteElementContainers.QuadratureField`
  * `JxWs::FiniteElementContainers.QuadratureField`
