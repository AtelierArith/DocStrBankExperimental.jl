```
format_sse_message(data::String; event::Union{String, Nothing} = nothing, id::Union{String, Nothing} = nothing)
```

適切にフォーマットされたサーバー送信イベント (SSE) 文字列を作成します。

# 引数

  * `data`: 送信するデータ。これは文字列である必要があります。データ内の改行文字は、別々の "data:" 行に置き換えられます。
  * `event`: (オプション) 送信するイベントのタイプ。提供されない場合、イベントタイプは送信されません。改行文字を含んではいけません。
  * `retry`: (オプション) イベントの再接続時間（ミリ秒単位）。提供されない場合、再接続時間は送信されません。整数である必要があります。
  * `id`: (オプション) イベントのID。提供されない場合、IDは送信されません。改行文字を含んではいけません。

# 注意事項

この関数は、クライアントにイベントを送信するためのサーバー送信イベント (SSE) 仕様に従っています。
