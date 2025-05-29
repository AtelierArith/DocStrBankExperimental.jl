```
send_message(
container::ContainerInterface,
content::Any,
address::Address,
sender_id::Union{Nothing,String}=nothing;
kwargs...,
```

)

指定されたコンテナ `container` を使用して、指定されたアドレスにメッセージ `message` を送信します。さらに、メッセージの内部メタデータを埋めるために、追加のキーワード引数を定義できます。
