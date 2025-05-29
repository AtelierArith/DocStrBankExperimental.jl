```
execute_webhook(
    c::Client,
    webhook::Integer,
    token::AbstractString;
    wait::Bool=false,
    kwargs...,
) -> Message
```

Execute a [`Webhook`](@ref). If `wait` is not set, no [`Message`](@ref) is returned. More details [here](https://discordapp.com/developers/docs/resources/webhook#execute-webhook).
