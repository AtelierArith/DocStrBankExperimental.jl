```
execute_slack_compatible_webhook(
    c::Client,
    webhook::Integer,
    token::AbstractString;
    wait::Bool=true,
    kwargs...,
)
```

Execute a Slack [`Webhook`](@ref). More details [here](https://discordapp.com/developers/docs/resources/webhook#execute-slackcompatible-webhook).
