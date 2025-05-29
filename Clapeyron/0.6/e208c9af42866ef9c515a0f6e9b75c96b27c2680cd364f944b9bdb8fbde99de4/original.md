```
reference_state(model)::Union{ReferenceState,Nothing}
```

Returns the reference state of the input model, if available. Returns `nothing` otherwise.

## Examples

```julia-repl
julia> reference_state(PCSAFT("water"))
false

julia> has_reference_state(PCSAFT("water",idealmodel = ReidIdeal))
true

julia> reference_state(PCSAFT("water",idealmodel = MonomerIdeal)) #has reference state, it is not initialized.
ReferenceState(String[], Float64[], Float64[], NaN, NaN, Float64[], Float64[], Float64[], :unknown, :no_set)

julia> reference_state(PCSAFT("water",idealmodel = MonomerIdeal, reference_state = ReferenceState(:nbp))) #has an initialized reference state
ReferenceState(["water"], [33107.133379491206], [17.225988924236503], NaN, NaN, [0.0], [0.0], [0.0], :unknown, :nbp)
```
