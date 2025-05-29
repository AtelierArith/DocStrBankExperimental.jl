```
useglobally!(tg::TelegramClient)
```

`tg`をすべての`Telegram.API`関数のデフォルトクライアントとして設定します。

# 例

```julia
tg = TelegramClient(ENV["TG_TOKEN"])
useglobally!(tg)

getMe() # このコマンドでは新しいクライアントがデフォルトで使用されます。
```
