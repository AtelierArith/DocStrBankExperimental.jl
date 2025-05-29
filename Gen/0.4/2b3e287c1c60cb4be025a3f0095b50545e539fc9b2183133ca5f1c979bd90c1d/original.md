```
translator = SimpleExtendingTraceTranslator(;
    p_new_args::Tuple = (),
    p_argdiffs::Tuple = (),
    new_observations::ChoiceMap = EmptyChoiceMap(),
    q_forward::GenerativeFunction,
    q_forward_args::Tuple  = ())
```

Constructor for a simple extending trace translator.

Run the translator with:

```
(output_trace, log_weight) = translator(input_trace)
```
