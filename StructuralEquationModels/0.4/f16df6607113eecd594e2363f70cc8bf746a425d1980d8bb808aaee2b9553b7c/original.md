```
(1) replace_observed(model::AbstractSemSingle; kwargs...)

(2) replace_observed(model::AbstractSemSingle, observed; kwargs...)
```

Return a new model with swaped observed part.

# Arguments

  * `model::AbstractSemSingle`: model to swap the observed part of.
  * `kwargs`: additional keyword arguments; typically includes `data` and `specification`
  * `observed`: Either an object of subtype of `SemObserved` or a subtype of `SemObserved`

# Examples

See the online documentation on [Replace observed data](@ref).
