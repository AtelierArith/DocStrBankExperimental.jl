```
dofres = getdof(state;[class=:X],field=:somefield,nodID=[nodids...],[orders=[0]])
```

Obtain the value of dofs of the same class and field, at various nodes and for various states.

If `state` is a vector, the output `dofres` has size `(ndof,nder+1,nstate)`. If `state` is a scalar, the output `dofres` has size `(ndof,nder+1)`.

See also: [`getresult`](@ref), [`addnode!`](@ref), [`solve`](@ref)
