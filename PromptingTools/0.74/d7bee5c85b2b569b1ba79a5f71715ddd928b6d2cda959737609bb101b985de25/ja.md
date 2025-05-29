```
aiclassify(tracer_schema::AbstractTracerSchema, prompt::ALLOWED_PROMPT_TYPE;
    tracer_kwargs = NamedTuple(), model = "", kwargs...)
```

通常の `aiclassify` 呼び出しをトレーシング/コールバックシステムでラップします。トレーサー/コールバックシステムに必要な情報を提供するために `tracer_kwargs` を使用してください（例：`parent_id`、`thread_id`、`run_id`）。

ロジック：

  * `initialize_tracer` を呼び出す
  * `aiclassify` を呼び出す（`tracer_schema.schema` を使用）
  * `finalize_tracer` を呼び出す
