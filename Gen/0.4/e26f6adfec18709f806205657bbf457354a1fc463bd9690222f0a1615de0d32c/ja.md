```
translator = DeterministicTraceTranslator(;
    p_new::GenerativeFunction, p_args::Tuple=();
    new_observations::ChoiceMap=EmptyChoiceMap()
    f::TraceTransformDSLProgram)
```

決定論的トレース翻訳者のコンストラクタ。

翻訳者を実行するには：

```
(output_trace, log_weight) = translator(input_trace)
```
