```
aigenerate(tracer_schema::AbstractTracerSchema, prompt::ALLOWED_PROMPT_TYPE;
    tracer_kwargs = NamedTuple(), model = "", return_all::Bool = false, kwargs...)
```

通常の `aigenerate` 呼び出しをトレーシング/コールバックシステムでラップします。`tracer_kwargs` を使用して、トレーサー/コールバックシステムに必要な情報（例：`parent_id`、`thread_id`、`run_id`）を提供します。

ロジック：

  * `initialize_tracer` を呼び出す
  * `aigenerate` を呼び出す（`tracer_schema.schema` を使用）
  * `finalize_tracer` を呼び出す

# 例

```julia
wrap_schema = PT.TracerSchema(PT.OpenAISchema())
msg = aigenerate(wrap_schema, "Say hi!"; model = "gpt4t")
msg isa TracerMessage # true
msg.content # メッセージのようにコンテンツにアクセス
PT.pprint(msg) # メッセージを整形して表示
```

メッセージのベクターで動作し、トレーサーでないものだけを変換します。例えば、

```julia
wrap_schema = PT.TracerSchema(PT.OpenAISchema())
conv = aigenerate(wrap_schema, "Say hi!"; model = "gpt4t", return_all = true)
all(PT.istracermessage, conv) #true
```
