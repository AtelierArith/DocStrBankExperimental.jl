```
connect(
    connection::MQTTConnection,
    server_name::String,
    port::Integer,
    client_id::String;
    clean_session::Bool = true,
    on_connection_interrupted::Union{OnConnectionInterrupted,Nothing} = nothing,
    on_connection_resumed::Union{OnConnectionResumed,Nothing} = nothing,
    reconnect_min_timeout_secs::Integer = 5,
    reconnect_max_timeout_secs::Integer = 60,
    keep_alive_secs::Integer = 1200,
    ping_timeout_ms::Integer = 3000,
    protocol_operation_timeout_ms::Integer = 0,
    will::Union{Will,Nothing} = nothing,
    username::Union{String,Nothing} = nothing,
    password::Union{String,Nothing} = nothing,
    socket_options = Ref(aws_socket_options(AWS_SOCKET_STREAM, AWS_SOCKET_IPV6, 5000, 0, 0, 0, false)),
    alpn_list::Union{Vector{String},Nothing} = nothing,
    use_websockets::Bool = false,
    websocket_handshake_transform = nothing, # TODO union type
    proxy_options = nothing, # TODO union type
)
```

サーバーへの実際の接続を開く（非同期）。

引数:

  * `connection (MQTTConnection)`: 使用する接続。
  * `server_name (String)`: 接続するサーバー名。
  * `port (Integer)`: 接続するサーバーポート。
  * `client_id (String)`: CONNECTパケットに配置するID。すべてのデバイス/クライアントで一意である必要があります。IDがすでに使用されている場合、他のクライアントは切断されます。
  * `clean_session (Bool) (default=true)`: 再接続ごとにクリーンセッションを開始するかどうか。`true`の場合、サーバーは再接続ごとにすべてのサブスクリプションを忘れます。`false`に設定すると、サーバーに既存のセッションを再開するか、接続が失われた後に再開できる新しいセッションを開始するようリクエストします。接続コールバック内の`session_present`ブール値は、既存のセッションが正常に再開されたかどうかを通知します。既存のセッションが再開されると、サーバーは以前のサブスクリプションを記憶し、クライアントがオフラインの間に公開されたメッセージ（QoSレベル1以上）を送信します。
  * `on_connection_interrupted (Union{OnConnectionInterrupted,Nothing}) (default=nothing)`: MQTT接続が失われるたびに呼び出されるオプションのコールバック。MQTTクライアントは自動的に再接続を試みます。[`OnConnectionInterrupted`](@ref)を参照してください。
  * `on_connection_resumed (Union{OnConnectionResumed,Nothing}) (default=nothing)`: MQTT接続が自動的に再開されるたびに呼び出されるオプションのコールバック。[`OnConnectionResumed`](@ref)を参照してください。
  * `reconnect_min_timeout_secs (Integer) (default=5)`: 再接続試行の間に待機する最小時間。`reconnect_max_timeout_secs`以下である必要があります。待機は最小から始まり、各試行ごとに倍増し、最大に達するまで続きます。
  * `reconnect_max_timeout_secs (Integer) (default=60)`: 再接続試行の間に待機する最大時間。`reconnect_min_timeout_secs`以上である必要があります。待機は最小から始まり、各試行ごとに倍増し、最大に達するまで続きます。
  * `keep_alive_secs (Integer) (default=1200)`: CONNECTパケットに送信するキープアライブ値（秒）。この間隔で自動的にPINGが送信されます。サーバーは、1.5倍のこの値の後にPINGが受信されない場合、接続が失われたと見なします。この期間は`ping_timeout_ms`よりも長くする必要があります。
  * `ping_timeout_ms (Integer) (default=3000)`: クライアントが接続が無効であると見なす前にPING応答を待機するミリ秒。この期間は`keep_alive_secs`よりも短くする必要があります。
  * `protocol_operation_timeout_ms (Integer) (default=0)`: サーバーによる応答を必要とする操作の応答を待機するミリ秒。タイムアウトを無効にするにはゼロに設定します。そうでない場合、パケットがソケットに書き込まれた後、この時間内に応答が受信されないと操作は失敗します。これはPUBLISH（QoSレベルが0より大きい場合）およびUNSUBSCRIBEで機能します。
  * `will (Union{Will,Nothing}) (default=nothing)`: CONNECTパケットと共に送信するウィル。ウィルは、クライアントとの接続が予期せず失われたときにサーバーによって公開されます。
  * `username (Union{String,Nothing}) (default=nothing)`: 接続に使用するユーザー名。
  * `password (Union{String,Nothing}) (default=nothing)`: 接続に使用するパスワード。
  * `socket_options (Ref(aws_socket_options}) (default=Ref(aws_socket_options(AWS_SOCKET_STREAM, AWS_SOCKET_IPV6, 5000, 0, 0, 0, false)))`: オプションのソケットオプション。
  * `alpn_list (Union{Vector{String},Nothing}) (default=nothing)`: 接続固有のアプリケーション層プロトコルネゴシエーション（ALPN）リスト。このリストは、この接続が行われたクライアントのTLSコンテキスト上の任意のALPNリストを上書きします。すべてのシステムでALPNがサポートされているわけではありません。[`aws_tls_is_alpn_available`](https://octogonapus.github.io/LibAWSCRT.jl/dev/#LibAWSCRT.aws_tls_is_alpn_available-Tuple%7B%7D)を参照してください。
  * `use_websockets (Bool) (default=false)`: # TODO 未実装
  * `websocket_handshake_transform (nothing) (default=nothing)`: # TODO 未実装
  * `proxy_options (nothing) (default=nothing)`: # TODO 未実装

接続が成功または失敗したときに完了するタスクを返します。

接続が成功した場合、タスクには次のキーを含む辞書が含まれます:

  * `:session_present`: 既存のセッションを再開している場合は`true`、新しいセッションの場合は`false`

接続が失敗した場合、タスクは例外をスローします。

!!! note
    すべてのコールバックは同時に実行されます。コールバックの実装はスレッドセーフである必要があります。並行性の制限はありません。

