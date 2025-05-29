```
sendsms(msg; from, to, sid, auth_token)
```

Twilioを使用してテキストメッセージを送信します。

## 引数

  * `msg` 送信するメッセージ
  * `from` 送信元の電話番号
  * `to` 受信者の電話番号
  * `sid` TwilioアカウントのアカウントSID。指定されていない場合は、環境変数 `TWILIO_ACCOUNT_SID` を読み取ろうとします
  * `auth_token` Twilioアカウントの認証トークン。指定されていない場合は、環境変数 `TWILIO_AUTH_TOKEN` を読み取ろうとします

## 例

```julia-repl
julia> sendsms("Hello, World 🌍!", from="+1-202-555-0107", to="+1-512-555-0180")

julia> sendsms("With explicit sid and access token", from="+1-202-555-0107", to="+1-512-555-0180",
                sid="d5d7b014b05d54fa52647820a035089e", auth_token="bed7fe1af0d18dfd-100972663d58f196")
```
