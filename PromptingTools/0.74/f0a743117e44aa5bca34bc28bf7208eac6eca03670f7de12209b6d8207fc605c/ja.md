```
aiscan(tracer_schema::AbstractTracerSchema, prompt::ALLOWED_PROMPT_TYPE;
    tracer_kwargs = NamedTuple(), model = "", kwargs...)
```

通常の `aiscan` 呼び出しをトレーシング/コールバックシステムでラップします。`tracer_kwargs` を使用して、トレーサー/コールバックシステムに必要な情報（例：`parent_id`、`thread_id`、`run_id`）を提供します。

ロジック：

  * `initialize_tracer` を呼び出す
  * `aiscan` を呼び出す（`tracer_schema.schema` を使用）
  * `finalize_tracer` を呼び出す
