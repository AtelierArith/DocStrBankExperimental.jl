```
translator = SymmetricTraceTranslator(;
    q::GenerativeFunction,
    q_args::Tuple = (),
    involution::Union{TraceTransformDSLProgram,Function})
```

対称トレーストランスレーターのコンストラクターです。

反転は、[`@transform`](@ref) マクロを介して構築されるか（推奨）、Julia 関数として提供されることができます。

トランスレーターを実行するには、次のようにします。

```
(output_trace, log_weight) = translator(input_trace; check=false, observations=EmptyChoiceMap())
```

`check` を使用して反転チェックを有効にします（これには、変換 `f` が [`is_involution!`](@ref) でマークされている必要があります）。

`check` が有効になっている場合、`observations` は観測されたランダムな選択を含む選択マップであり、チェックはさらにそれらが反転によって変更されないことを保証します。
