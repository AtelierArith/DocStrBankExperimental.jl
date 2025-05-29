```
InfiniteOpt.build_optimizer_model!(model::InfiniteOpt.InfiniteModel,
                                   key::Val{:TransData};
                                   check_support_dims::Bool = true)::Nothing
```

`model`を転写モデルとして転写モデルフィールド`model.optimizer_model`に保存し、`transcription_model`でアクセスできます。これにより、[`InfiniteOpt.clear_optimizer_model_build!`](@ref)を使用して既存の転写モデルがクリアされ、その後、[`build_transcription_model!`](@ref)を使用して新しいものが構築されます。
