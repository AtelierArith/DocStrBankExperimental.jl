```
transcription_expression(trans_model::JuMP.Model, expr, support::Vector{Float64})
```

Given the `expr` from an `InfiniteModel`, form its transcripted version in accordance with the variable mappings available in `trans_model` defined at `support`. This should only be used once all variables and measures have been transcribed (e.g., via [`transcribe_finite_variables!`](@ref)).
