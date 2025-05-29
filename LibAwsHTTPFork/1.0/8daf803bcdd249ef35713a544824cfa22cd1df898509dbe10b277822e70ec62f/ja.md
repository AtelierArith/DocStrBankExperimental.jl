```
aws_http_connection_close(connection)
```

接続のシャットダウンシーケンスを開始します。まだ開始されていない場合。この関数は、必要に応じてピアにHTTP/TLS/TCPシャットダウンメッセージを送信する可能性のあるシャットダウンタスクをEventLoopにスケジュールし、最終的には内部接続メモリへのアクセスを停止し、on_shutdown()コールバックを呼び出す原因となります。

接続の状態に関係なく、接続への参照を保持している限り、この関数を呼び出すことは安全です。

### プロトタイプ

```c
void aws_http_connection_close(struct aws_http_connection *connection);
```
