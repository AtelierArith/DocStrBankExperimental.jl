```
InfiniteOpt.build_optimizer_model!(model::InfiniteOpt.InfiniteModel,
                                   key::Val{:TransData};
                                   check_support_dims::Bool = true)::Nothing
```

Transcribe `model` and store it as a `TranscriptionModel` in the `model.optimizer_model` field which can be accessed with `transcription_model`. Ths clears the existing `TranscriptionModel` via [`InfiniteOpt.clear_optimizer_model_build!`](@ref) and then builds a new one using [`build_transcription_model!`](@ref).
