```
ReactionMethod(
    methodfn::Function,
    reaction::AbstractReaction,
    name::String,
    varlists::Tuple{Vararg{AbstractVarList}},
    p, 
    operatorID::Vector{Int64}, 
    domain::AbstractDomain; 
    preparefn = (m, vardata) -> vardata
) -> m::ReactionMethod
```

Defines a callback function `methodfn` with Variables `varlists`, to be called from the Model framework either during setup or as part of the main loop.

# Fields

  * `methodfn`: callback from Model framework
  * `reaction`: the Reaction that created this ReactionMethod
  * `name`: a descriptive name, eg generated from the name of methodfn
  * `varlists`: Tuple of VarLists, each representing a list of [`VariableReaction`](@ref)s.     Corresponding Variable accessors `vardata` (views on Arrays) will be provided to the `methodfn` callback.     NB: not concretely typed to reduce compile time, as not performance-critical
  * `p`: optional context field (of arbitrary type) to store data needed by methodfn.
  * `operatorID`
  * `domain`
  * `preparefn`: preparefn(m::ReactionMethod, vardata::Tuple) -> modified_vardata::Tuple      optionally modify `vardata` to eg add buffers. NB: not concretely typed as not performance-critical

# methodfn

The `methodfn` callback is:

```
methodfn(m::ReactionMethod, pars, vardata::Tuple, cellrange::AbstractCellRange, modelctxt)
```

or (if Parameters are not required):

```
methodfn(m::ReactionMethod, vardata::Tuple, cellrange::AbstractCellRange, modelctxt)
```

With arguments:

  * `m::ReactionMethod`: context is available as `m.reaction::AbstractReaction` (the Reaction that defined the `ReactionMethod`), and `m.p` (an arbitrary extra context field supplied when `ReactionMethod` created).
  * `pars`: a struct with Parameters as fields (current just the ParametersTuple defined as `reaction.pars`)
  * `vardata`: A Tuple of collections of views on Domain data arrays corresponding to [`VariableReaction`](@ref)s defined by `varlists`
  * `cellrange::AbstractCellRange`: range of cells to calculate.
  * `modelctxt`:

      * for a setup method, `:setup`, `:initial_value` or `:norm_value` defining the type of setup requested
      * for a main loop method `deltat` providing timestep information eg for rate throttling.

# preparefn

An optional `preparefn` callback can be supplied eg to allocate buffers that require knowledge of the data types of `vardata` or to cache expensive calculations:

```
preparefn(m::ReactionMethod, vardata::Tuple) -> modified_vardata::Tuple
```

This is called after model arrays are allocated, and prior to setup.
