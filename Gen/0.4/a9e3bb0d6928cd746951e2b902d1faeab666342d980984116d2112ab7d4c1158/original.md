```
translator = GeneralTraceTranslator(;
    p_new::GenerativeFunction,
    p_new_args::Tuple = (),
    new_observations::ChoiceMap = EmptyChoiceMap(),
    q_forward::GenerativeFunction,
    q_forward_args::Tuple  = (),
    q_backward::GenerativeFunction,
    q_backward_args::Tuple  = (),
    f::TraceTransformDSLProgram)
```

Constructor for a general trace translator.

Run the translator with:

```
(output_trace, log_weight) = translator(input_trace; check=false, prev_observations=EmptyChoiceMap())
```

Use `check` to enable a bijection check (this requires that the transform `f` has been paired with its inverse using [`pair_bijections!](@ref) or [`is_involution!`](@ref)).

If `check` is enabled, then `prev_observations` is a choice map containing the observed random choices in the previous trace.
