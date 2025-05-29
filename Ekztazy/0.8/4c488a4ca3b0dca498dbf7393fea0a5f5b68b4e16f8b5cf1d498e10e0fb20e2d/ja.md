```
execute_webhook(
    c::Client,
    webhook::Integer,
    token::AbstractString;
    wait::Bool=false,
    kwargs...,
) -> Message
```

[`Webhook`](@ref)を実行します。`wait`が設定されていない場合、[`Message`](@ref)は返されません。詳細は[こちら](https://discordapp.com/developers/docs/resources/webhook#execute-webhook)を参照してください。
