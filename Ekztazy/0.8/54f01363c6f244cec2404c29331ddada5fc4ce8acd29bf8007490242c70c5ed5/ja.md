```
execute_slack_compatible_webhook(
    c::Client,
    webhook::Integer,
    token::AbstractString;
    wait::Bool=true,
    kwargs...,
)
```

Slackの[`Webhook`](@ref)を実行します。詳細は[こちら](https://discordapp.com/developers/docs/resources/webhook#execute-slackcompatible-webhook)をご覧ください。
