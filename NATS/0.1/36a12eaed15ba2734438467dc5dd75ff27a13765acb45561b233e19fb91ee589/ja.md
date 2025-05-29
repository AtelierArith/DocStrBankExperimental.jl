```julia
publish(connection, subject; ...)
publish(connection, subject, data; reply_to)

```

`data`を`subject`に公開します。ペイロードは、`mime` `application/nats-payload`を受け取る`show`メソッドを使用して取得され、ヘッダーは、`mime` `application/nats-headers`を受け取る`show`メソッドを使用して取得されます。

`String`型に対しては、事前定義された変換が定義されています。ヘッダーを公開するためには、文字列のペアのベクターを受け取るタプルからの変換が定義されています。

オプションのパラメータ：

  * `reply_to`: 結果が公開されるべきサブジェクト

例：

```
    publish(nc, "some_subject", "Some payload")
    publish("some_subject", ("Some payload", ["some_header" => "Example header value"]))
```
