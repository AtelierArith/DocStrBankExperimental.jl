```
export_responses_by_token(client, survey_id, token, sink; kwargs...)
```

Export responses from remote survey with `survey_id` as a Tables.jl compatible `sink`, e.g. `DataFrame`.
