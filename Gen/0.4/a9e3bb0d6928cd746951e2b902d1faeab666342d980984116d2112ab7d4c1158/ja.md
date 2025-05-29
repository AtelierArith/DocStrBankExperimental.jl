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

一般的なトレース翻訳者のコンストラクタ。

翻訳者を実行するには：

```
(output_trace, log_weight) = translator(input_trace; check=false, prev_observations=EmptyChoiceMap())
```

`check`を使用して双射チェックを有効にします（これには、変換`f`が[`pair_bijections!](@ref)または[`is_involution!`](@ref)を使用してその逆とペアになっている必要があります）。

`check`が有効になっている場合、`prev_observations`は前のトレースで観測されたランダムな選択を含む選択マップです。
