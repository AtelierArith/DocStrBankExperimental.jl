```
Muscade.draw(ElementType,axe,o, Λ,X,U,A,t,SP,dbg;kwargs...)
```

Inputs are:

  * `ElementType`, the method must dispatch on this `DataType`.
  * `axe`, a `GLMakie` axe
  * `o` a `AbstractVector` of element objects, of length `nel`.
  * `Λ` a matrix of size `(nXdof,nel)`
  * `X` a `NTuple` of matrices of size `(nXdof,nel)`
  * `U` a `NTuple` of matrices of size `(nUdof,nel)`
  * `A` a matrix of size `(nAdof,nel)`
  * `t` time
  * `SP` solver parameters
  * `dbg` debuging information
  * `kwargs` a `NamedTuple` containing the keyword arguments provided by the user. See [`default`](@ref).

See also: [`lagrangian`](@ref), [`residual`](@ref), [`doflist`](@ref)
