```
execute_github_compatible_webhook(
    c::Client,
    webhook::Integer,
    token::AbstractString;
    wait::Bool=true,
    kwargs...,
)
```

Execute a Github [`Webhook`](@ref). More details [here](https://discordapp.com/developers/docs/resources/webhook#execute-githubcompatible-webhook).
