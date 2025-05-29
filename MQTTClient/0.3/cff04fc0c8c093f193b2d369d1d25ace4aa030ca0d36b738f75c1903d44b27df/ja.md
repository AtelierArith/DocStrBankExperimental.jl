```
Connection{T <: AbstractIOConnection}
```

`Connection`構造体は、JuliaにおいてMQTTクライアントがMQTTブローカーに接続するために必要な設定と接続の詳細をカプセル化します。この構造体は、TCPとUnixドメインソケット（UDS）の2種類の接続プロトコルをサポートしており、どちらも`AbstractIOConnection`のサブタイプです。この構造体には、プロトコルタイプ、キープアライブ間隔、クライアントID、ユーザー資格情報、ウィルメッセージ（クライアントが予期せず切断された場合にブローカーによって送信されるメッセージ）、およびセッションがクリーンであるかどうかを示すフラグが含まれています。`Connection`コンストラクタは、各フィールドのデフォルトまたは指定された値を使用して柔軟にインスタンス化できるようにし、MQTTクライアントとブローカーの相互作用に特有の要件に合わせた接続パラメータの簡単な設定を可能にします。

## フィールド

  * `protocol::T`: 基本となるIO接続。
  * `keep_alive::Int64`: キープアライブ時間（秒）。
  * `client_id::String`: クライアント識別子。
  * `user::User`: ユーザー資格情報。
  * `will::Message`: 最後のウィルメッセージ。
  * `clean_session::Bool`: クリーンセッションを開始するかどうか。

## コンストラクタ

`Connection(protocol::T; keep_alive::Int64=32, client_id::String=randstring(8), user::User=User("", ""), will::Message=Message(false, 0x00, false, "", UInt8[]), clean_session::Bool=true) where T <: AbstractIOConnection`は、指定されたプロトコルとオプションのキーワード引数を使用して新しい`Connection`オブジェクトを構築します。

`Connection(protocol::T, keep_alive::Int64, client_id::String, user::User, will::Message, clean_session::Bool) where T <: AbstractIOConnection`は、指定された引数を使用して新しい`Connection`オブジェクトを構築します。

### デフォルトおよびカスタム値を使用したTCPプロトコルの例

```julia
tcp_connection = Connection(
    TCP(Sockets.localhost, 1883);       # localhostとポート1883を使用したTCP
    keep_alive=60,                      # 60秒のカスタムキープアライブ間隔
    client_id="my_mqtt_client",         # カスタムクライアントID
    user=User("username", "password"),  # カスタムユーザー資格情報
    will=Message(false, 0x01, false, "last/will/topic", UInt8[]),  # カスタムウィルメッセージ
    clean_session=true,                  # デフォルトのクリーンセッションフラグ
)
```

### すべてカスタム値を使用したUDSプロトコルの例

```julia
uds_connection_full = Connection(
    UDS("/var/run/mqtt.sock"),          # 指定されたソケットパスを使用したUDS
    45,                                 # 45秒のカスタムキープアライブ間隔
    "another_client",                   # カスタムクライアントID
    User("user", "pass"),               # カスタムユーザー資格情報
    Message(true, 0x00, true, "will/topic", UInt8[1, 2, 3]),  # カスタムウィルメッセージ
    false,                               # カスタムクリーンセッションフラグ
)
```
