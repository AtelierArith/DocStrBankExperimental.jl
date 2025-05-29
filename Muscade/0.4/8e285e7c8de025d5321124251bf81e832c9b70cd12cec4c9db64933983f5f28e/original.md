```
eleres = getresult(state,req,els)
```

Obtain an array of nested `NamedTuples` and `NTuples` of element results. `req` is a request defined using `@request`. `state` a vector of `State`s or a single `State`. `els` can be either

  * a vector of `EleID`s (obtained from `addelement!`) all corresponding to the same concrete element type
  * a concrete element type (see [`eletyp`](@ref)).

If `state` is a vector, the output `dofres` has size `(nele,nstate)`. If `state` is a scalar, the output `dofres` has size `(nele)`.

See also: [`getdof`](@ref), [`@request`](@ref), [`@espy`](@ref), [`addelement!`](@ref), [`solve`](@ref), [`eletyp`](@ref)
