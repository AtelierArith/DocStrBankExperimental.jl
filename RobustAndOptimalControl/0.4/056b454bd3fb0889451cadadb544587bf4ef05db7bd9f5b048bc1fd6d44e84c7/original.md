```
diskmargin(P::LTISystem, C::LTISystem, σ, w::AbstractVector, args...; kwargs...)
```

Simultaneuous diskmargin at outputs, inputs and input/output simultaneously of `P`.  Returns a named tuple with the fields `input, output, simultaneous_input, simultaneous_output, simultaneous` where `input` and `output` represent loop-at-a-time margins, `simultaneous_input` is the margin for simultaneous perturbations on all inputs and `simultaneous` is the margin for perturbations on all inputs and outputs simultaneously.

Note: simultaneous margins are more conservative than single-loop margins and are likely to be much lower than the single-loop margins. Indeed, with several simultaneous perturbations, it's in general easier to make the system unstable. It's not uncommon for a simultaneous margin involving two signals to be on the order of half the size of the single-loop margins.

See also [`ncfmargin`](@ref) and [`loop_diskmargin`](@ref).
