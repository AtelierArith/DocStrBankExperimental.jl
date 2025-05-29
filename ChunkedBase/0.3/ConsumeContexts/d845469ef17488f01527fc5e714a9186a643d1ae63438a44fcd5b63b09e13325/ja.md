```
consume!(consume_ctx::AbstractConsumeContext, payload::ParsedPayload{<:AbstractResultBuffer, <:AbstractParsingContext})
```

`AbstractConsumeContext`をオーバーライドして、`AbstractResultBuffer`内の解析された結果を処理するためのカスタムロジックを提供します。このメソッドは、対応する`task_buf`がポピュレートされた直後に、複数のタスクから並行して呼び出されます。`task_buf`はチャンクごとに一度だけ埋められ、同時に一つのタスクによってのみアクセスされます。

[`consume!`](@ref)、[`setup_tasks!`](@ref)、[`setup_tasks!`](@ref)、[`cleanup`](@ref)、[`AbstractResultBuffer`](@ref)も参照してください。
