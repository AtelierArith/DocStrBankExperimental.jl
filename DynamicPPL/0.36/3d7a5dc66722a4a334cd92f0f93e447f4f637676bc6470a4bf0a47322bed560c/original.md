```
struct VarInfo{Tmeta,Tlogp} <: AbstractVarInfo
    metadata::Tmeta
    logp::Base.RefValue{Tlogp}
    num_produce::Base.RefValue{Int}
end
```

A light wrapper over some kind of metadata.

The type of the metadata can be one of a number of options. It may either be a `Metadata` or a `VarNamedVector`, *or*, it may be a `NamedTuple` which maps symbols to `Metadata` or `VarNamedVector` instances. Here, a *symbol* refers to a Julia variable and may consist of one or more `VarName`s which appear on the left-hand side of tilde statements. For example, `x[1]` and `x[2]` both have the same symbol `x`.

Several type aliases are provided for these forms of VarInfos:

  * `VarInfo{<:Metadata}` is `UntypedVarInfo`
  * `VarInfo{<:VarNamedVector}` is `UntypedVectorVarInfo`
  * `VarInfo{<:NamedTuple}` is `NTVarInfo`

The NamedTuple form, i.e. `NTVarInfo`, is useful for maintaining type stability of model evaluation. However, the element type of NamedTuples are not contained in its type itself: thus, there is no way to use the type system to determine whether the elements of the NamedTuple are `Metadata` or `VarNamedVector`.

Note that for NTVarInfo, it is the user's responsibility to ensure that each symbol is visited at least once during model evaluation, regardless of any stochastic branching.
