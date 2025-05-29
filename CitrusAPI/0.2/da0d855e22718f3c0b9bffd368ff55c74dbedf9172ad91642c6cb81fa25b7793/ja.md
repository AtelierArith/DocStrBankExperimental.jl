```
export_responses(client, survey_id, sink; kwargs...)
```

リモートサーベイから `survey_id` を使用して、`DataFrame` などの Tables.jl 互換の `sink` に応答をエクスポートします。
