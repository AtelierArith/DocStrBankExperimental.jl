```
termination_status_message(status)
```

`status`に関連するメッセージの文字列を返します。

[`TerminationStatusCode`](@ref)を参照してください。

### 例:

```julia-repl
julia> termination_status_message(Metaheuristics.ITERATION_LIMIT)
"最大反復回数を超えました。"

julia> termination_status_message(optimize(f, bounds))
"最大反復回数を超えました。"

julia> termination_status_message(ECA())
"不明な停止理由です。"
```
