```
modify_webhook_with_token(
    c::Client,
    webhook::Integer,
    token::AbstractString;
    kwargs...,
) -> Webhook
```

トークンを使用して[`Webhook`](@ref)を変更します。詳細は[こちら](https://discordapp.com/developers/docs/resources/webhook#modify-webhook)を参照してください。
