```
run_bot(f::Function, [tg::TelegramClient]; timeout = 10, brute_force_alive = false, offset = -1)
```

Run telegram bot, which executes function `f` repeatedly.

# Arguments

  * `f`: function to run with the bot. As an input it receive [Message](https://core.telegram.org/bots/api#message) in the form of JSON3 object.
  * `tg`: Telegram client, if not set then global telegram client is used.
  * `timeout`: timeout limit of messages, defines when longpoll messages should be interrupted
  * `brute_force_alive`: despite all measures, messages sometimes "hangs". You may use this argument to wake up telegram server regularly. When this option is set to `true` it works, but it is not recommended, since it makes additional calls. Consider this feature experimental and use at your own risk.
  * `offset`: telegram message offset, useful if you have processed messages, but bot was interrupted and messages state was lost.
