```
TLSConnectionOptions(
    client_tls_context::ClientTLSContext,
    alpn_list::Union{Vector{String},Nothing} = nothing,
    server_name::Union{String,Nothing} = nothing,
)
```

接続固有のTLSオプション。TLSコンテキストは高価なオブジェクトですが、このオブジェクトは安価です。

引数:

  * `client_tls_context (ClientTLSContext)`: TLSコンテキスト。コンテキストは多くの接続で共有できます。
  * `alpn_list (Union{Vector{String},Nothing}) (default=nothing)`: 接続固有のアプリケーションレイヤープロトコルネゴシエーション（ALPN）リスト。この接続が作成されたクライアントのTLSコンテキストにあるALPNリストを上書きします。ALPNはすべてのシステムでサポートされているわけではありません。詳細は[`aws_tls_is_alpn_available`](https://octogonapus.github.io/LibAWSCRT.jl/dev/#LibAWSCRT.aws_tls_is_alpn_available-Tuple%7B%7D)を参照してください。
  * `server_name (Union{String,Nothing}) (default=nothing)`: TLSサーバー名インジケーション（SNI）の名前。x.509検証にも使用されます。
