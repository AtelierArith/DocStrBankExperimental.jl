```
connection(f; kwargs...)

connection(;
    virtualhost = "/",
    host = "localhost",
    port = AMQPClient.AMQP_DEFAULT_PORT,
    framemax = 0,
    heartbeat = true,
    keepalive = DEFAULT_KEEPALIVE_SECS,
    send_queue_size = CONN_MAX_QUEUED,
    auth_params = AMQPClient.DEFAULT_AUTH_PARAMS,
    channelmax = AMQPClient.DEFAULT_CHANNELMAX,
    connect_timeout = AMQPClient.DEFAULT_CONNECT_TIMEOUT,
    amqps = nothing
)
```

AMQPサーバーへの新しい接続を作成します。後でチャネルを開くために使用できる接続を返します。Juliaのdoブロック構文を使用して接続を作成し、その後閉じることができます。

キーワード引数:

  * `host`: 接続するメッセージサーバーのホスト。デフォルトは "localhost"。
  * `port`: 接続するメッセージサーバーのポート。デフォルトはAMQPのデフォルトポート。
  * `virtualhost`: 接続する仮想ホスト。デフォルトは "/"。
  * `amqps`: AMQPSで接続する場合に使用するTLSオプション。`amqps_configure`を参照。
  * `connect_timeout`: 課すTCP接続タイムアウト。デフォルトは `AMQPClient.DEFAULT_CONNECT_TIMEOUT`。
  * `framemax`: 使用する最大フレームサイズ。デフォルトは0で、制限なしを意味します。
  * `heartbeat`: ハートビートを有効にするには `true`、無効にするには `false`。正の整数に設定することもでき、その場合はハートビートの間隔（秒）になります。デフォルトは `true`。`false`の場合、死んだ接続を検出するために `keepalive` が有効になっていることを確認してください。このパラメータはサーバーと交渉されます。
  * `keepalive`: TCPキープアライブを有効にするには `true`、無効にするには `false`。正の整数に設定することもでき、その場合はキープアライブの間隔（秒）になります。デフォルトは `DEFAULT_KEEPALIVE_SECS`。
  * `send_queue_size`: メッセージが排出されるまで送信APIをブロックする前にメモリにバッファリングするアイテムの最大数。デフォルトは CONN*MAX*QUEUED。
  * `auth_params`: 接続を認証するために使用するパラメータ。デフォルトは AMQPClient.DEFAULT*AUTH*PARAMS。
  * `channelmax`: サーバーと交渉する最大チャネル数。デフォルトは AMQPClient.DEFAULT_CHANNELMAX。
