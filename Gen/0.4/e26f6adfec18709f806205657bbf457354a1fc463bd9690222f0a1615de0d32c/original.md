```
translator = DeterministicTraceTranslator(;
    p_new::GenerativeFunction, p_args::Tuple=();
    new_observations::ChoiceMap=EmptyChoiceMap()
    f::TraceTransformDSLProgram)
```

Constructor for a deterministic trace translator.

Run the translator with:

```
(output_trace, log_weight) = translator(input_trace)
```
