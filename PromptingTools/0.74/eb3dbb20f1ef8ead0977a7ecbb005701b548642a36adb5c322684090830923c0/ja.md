```
aiembed(tracer_schema::AbstractTracerSchema,
    doc_or_docs::Union{AbstractString, AbstractVector{<:AbstractString}}, postprocess::Function = identity;
    tracer_kwargs = NamedTuple(), model = "", kwargs...)
```

通常の `aiembed` 呼び出しをトレーシング/コールバックシステムでラップします。`tracer_kwargs` を使用して、トレーサー/コールバックシステムに必要な情報（例：`parent_id`、`thread_id`、`run_id`）を提供します。

ロジック：

  * `initialize_tracer` を呼び出す
  * `aiembed` を呼び出す（`tracer_schema.schema` を使用）
  * `finalize_tracer` を呼び出す
