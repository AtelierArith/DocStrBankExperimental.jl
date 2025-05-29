```
MicroTC(
    config::MicroTC_Config,
    train_corpus::AbstractVector,
    train_y;
    textconfig=config.textconfig,
    verbose=true)
MicroTC(config::MicroTC_Config, textmodel::TextModel, train_X::AbstractVector{S}, train_y; verbose=true) where {S<:SVEC}
```

指定されたデータセットと構成に基づいてMicroTCモデルを作成します。
