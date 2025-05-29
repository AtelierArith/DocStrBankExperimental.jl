```
aws_http_connection_make_request(client_connection, options)
```

クライアント接続を使用してリクエストを送信するストリームを作成します。ストリームが作成されても、リクエストは自動的に送信され始めません。リクエストの実行を開始するには、[`aws_http_stream_activate`](@ref)を呼び出す必要があります。

この呼び出し中に`options`はコピーされます。

言語バインディングのヒント: `options`構造体をバインドしないでください。Javaのビルダーパターンや、Pythonの名前付きで多くのオプション引数を受け取る能力など、あなたの言語にとってより自然なものを使用してください。

注意: リクエストのヘッダーは、送信するメッセージのプロトコルが接続のプロトコルと一致する場合、そのまま送信されます。 - `user-agent`は追加されません。 - セキュリティチェックは強制されません。例: `referer`ヘッダーのプライバシーは、ヘッダーを追加するユーザーエージェントによって強制されるべきです。 - HTTP/1メッセージがHTTP/2接続で送信される場合、[`aws_http2_message_new_from_http1`](@ref)が内部で適用されます。 - HTTP/2メッセージがHTTP/1接続で送信される場合、変更は行われません。

### プロトタイプ

```c
struct aws_http_stream *aws_http_connection_make_request( struct aws_http_connection *client_connection, const struct aws_http_make_request_options *options);
```
