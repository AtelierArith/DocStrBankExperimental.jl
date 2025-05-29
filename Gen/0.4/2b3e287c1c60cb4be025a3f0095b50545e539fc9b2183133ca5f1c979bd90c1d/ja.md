```
translator = SimpleExtendingTraceTranslator(;
    p_new_args::Tuple = (),
    p_argdiffs::Tuple = (),
    new_observations::ChoiceMap = EmptyChoiceMap(),
    q_forward::GenerativeFunction,
    q_forward_args::Tuple  = ())
```

シンプルな拡張トレーストランスレーターのコンストラクタ。

トランスレーターを実行するには：

```
(output_trace, log_weight) = translator(input_trace)
```
