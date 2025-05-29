```
export_responses_by_token(client, survey_id, token, sink; kwargs...)
```

リモート調査から `survey_id` を使用して、`DataFrame` などの Tables.jl 互換の `sink` に応答をエクスポートします。
