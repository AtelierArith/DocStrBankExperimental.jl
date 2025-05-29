```
translator = SymmetricTraceTranslator(;
    q::GenerativeFunction,
    q_args::Tuple = (),
    involution::Union{TraceTransformDSLProgram,Function})
```

Constructor for a symmetric trace translator.

The involution is either constructed via the [`@transform`](@ref) macro (recommended), or can be provided as a Julia function.

Run the translator with:

```
(output_trace, log_weight) = translator(input_trace; check=false, observations=EmptyChoiceMap())
```

Use `check` to enable the involution check (this requires that the transform `f` has been marked with [`is_involution!`](@ref)).

If `check` is enabled, then `observations` is a choice map containing the observed random choices, and the check will additionally ensure they are not mutated by the involution.
