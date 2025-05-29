```
describe(model,spec)
```

Print out information about `model`. `spec` can be 

  * an `EleID` to describe an element,
  * a `DofID` to describe a dof.
  * a `NodID` to describe a node,
  * `:doftyp` to obtain a list of doftypes,
  * `:dof` to obtain a list of dofs or
  * `:eletyp` for a list of element types.

See also: [`addelement!`](@ref), [`addnode!`](@ref)
