```
is_transcription_model(model::JuMP.Model)::Bool
```

`model` が `TranscriptionModel` の場合は true を返し、それ以外の場合は false を返します。

**例**

```julia-repl
julia> is_transcription_model(model)
true
```
