```julia
reply(f, connection, subject; queue_group, spawn)

```

`subject` に対するメッセージの返信を行います。`reply_to` フィールドからの `publish` を自動的に行う `subscribe` のように動作します。

オプションのキーワード引数は次の通りです：

  * `queue_group`: NATS サーバーはメッセージをキューグループのメンバー間で分配します
  * `spawn`: `true` の場合、各 `f` の呼び出しに対してタスクが生成されます。そうでない場合、メッセージは順次処理され、デフォルトは `false` です

# 例

```julia-repl
julia> sub = reply("FOO.REQUESTS") do msg
    "This is a reply payload."
end
NATS.Sub("FOO.REQUESTS", nothing, "jdnMEcJN")

julia> sub = reply("FOO.REQUESTS") do msg
    "This is a reply payload.", ["example_header" => "This is a header value"]
end
NATS.Sub("FOO.REQUESTS", nothing, "jdnMEcJN")

julia> unsubscribe(sub)
```
