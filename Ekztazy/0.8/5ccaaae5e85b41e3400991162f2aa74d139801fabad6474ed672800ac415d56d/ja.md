```
execute_github_compatible_webhook(
    c::Client,
    webhook::Integer,
    token::AbstractString;
    wait::Bool=true,
    kwargs...,
)
```

Github [`Webhook`](@ref) を実行します。詳細は [こちら](https://discordapp.com/developers/docs/resources/webhook#execute-githubcompatible-webhook) をご覧ください。
