```
codegen_expression(sig, ex; T = nothing, bindings::Optional{Bindings} = nothing)
```

Parse `ex` as an algebraic expression and generate a Julia expression which represents the corresponding computation. `sig` can be a [`SymbolicGA.Signature`](@ref), a signature integer or a signature string, tuple or tuple expression adhering to semantics of [`@ga`](@ref). See [`@ga`](@ref) for more information regarding the parsing and semantics applied to `ex`.

## Parameters

  * `T` specifies what type to use when reconstructing geometric entities from tuple components with [`construct`](@ref). If set to `nothing` and the result is in a non-flattened form (i.e. not annotated with an annotation of the type `<ex>::(0 + 2)`), then an appropriate [`KVector`](@ref) will be used depending on which type of geometric entity is returned; if multiple entities are present, a tuple of `KVector`s will be returned. If the result is in a flattened form, `T` will be set to `:Tuple` if unspecified.
  * `bindings` is a user-provided [`SymbolicGA.Bindings`](@ref) which controls what expansions are carried out on the raw Julia expression before conversion to an algebraic expression.
