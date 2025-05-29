```
create_client_with_mtls(cert_data, pk_data; kwargs...)
```

クライアントモードで相互TLSを使用するために構成されたオプションを作成します。両方のバッファはPKCS #7 PEMアーマードとして扱われます。

引数:

  * `cert_data (String)`: 証明書の内容
  * `pk_data (String)`: 秘密鍵の内容。
  * `ca_dirpath (Union{String,Nothing}) (default=nothing)`: 信頼された証明書を含むディレクトリへのパス。デフォルトの信頼ストアを上書きします。Unixでのみサポートされています。
  * `ca_filepath (Union{String,Nothing}) (default=nothing)`: PEMアーマードの信頼されたCA証明書のチェーンを含むファイルへのパス。
  * `ca_data (Union{String,Nothing}) (default=nothing)`: PEMアーマードの信頼されたCA証明書のチェーン。
  * `alpn_list (Union{Vector{String},Nothing}) (default=nothing)`: 設定されている場合、アプリケーション層プロトコルネゴシエーション（ALPN）で使用する名前。ALPNはすべてのシステムでサポートされているわけではありません。詳細は[`aws_tls_is_alpn_available`](https://octogonapus.github.io/LibAWSCRT.jl/dev/#LibAWSCRT.aws_tls_is_alpn_available-Tuple{})を参照してください。これは接続ごとにカスタマイズできます。詳細は[`TLSConnectionOptions`](@ref)を参照してください。
