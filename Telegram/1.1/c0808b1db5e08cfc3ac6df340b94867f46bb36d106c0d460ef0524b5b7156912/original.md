```
TelegramClient(token; chat_id, parse_mode, ep, use_globally = true)
```

Creates telegram client, which can be used to run telegram commands.

# Arguments

  * `token::String`: telegram token, which can be obtained in telegram from @BotFather.
  * `chat_id`: if set, used as default `chat_id` argument for all chat related commands. To get specific `chat_id`, send message to the bot in telegram application and use [`getUpdates`](@ref) command.
  * `parse_mode`: if set, used as default for text messaging commands.
  * `use_globally::Bool`: default `true`. If set to `true` then it current client can be used as default in all telegram commands.
  * `ep`: endpoint for telegram api. By default `https://api.telegram.org/bot` is used, but you may change it, if you are using proxy or for testing purposes.
