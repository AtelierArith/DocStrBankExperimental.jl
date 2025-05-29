```
useglobally!(tg::TelegramClient)
```

Set `tg` as default client in all `Telegram.API` functions. 

# Example

```julia
tg = TelegramClient(ENV["TG_TOKEN"])
useglobally!(tg)

getMe() # new client is used in this command by default.
```
