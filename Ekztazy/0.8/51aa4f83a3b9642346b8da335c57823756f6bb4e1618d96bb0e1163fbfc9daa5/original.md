```
modify_webhook_with_token(
    c::Client,
    webhook::Integer,
    token::AbstractString;
    kwargs...,
) -> Webhook
```

Modify a [`Webhook`](@ref) with a token. More details [here](https://discordapp.com/developers/docs/resources/webhook#modify-webhook).
