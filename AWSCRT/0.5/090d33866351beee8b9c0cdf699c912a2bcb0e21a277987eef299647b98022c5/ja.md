```
create_client_with_mtls_from_path(cert_filepath, pk_filepath; kwargs...)
```

クライアントモードで相互TLSを使用するために構成されたオプションを作成します。両方のファイルはPKCS #7 PEMアーマードとして扱われます。ディスクから読み込まれ、内部でバッファに保存されます。

引数:

  * `cert_filepath (String)`: 証明書ファイルへのパス。
  * `pk_filepath (String)`: プライベートキーファイルへのパス。
  * `ca_dirpath (Union{String,Nothing}) (default=nothing)`: デフォルトの信頼ストアをオーバーライドする信頼された証明書を含むディレクトリへのパス。Unixでのみサポートされています。
  * `ca_filepath (Union{String,Nothing}) (default=nothing)`: 信頼されたCA証明書のPEMアーマードチェーンを含むファイルへのパス。
  * `ca_data (Union{String,Nothing}) (default=nothing)`: 信頼されたCA証明書のPEMアーマードチェーン。
  * `alpn_list (Union{Vector{String},Nothing}) (default=nothing)`: 設定されている場合、アプリケーション層プロトコルネゴシエーション（ALPN）で使用する名前。ALPNはすべてのシステムでサポートされているわけではありません。詳細は[`aws_tls_is_alpn_available`](https://octogonapus.github.io/LibAWSCRT.jl/dev/#LibAWSCRT.aws_tls_is_alpn_available-Tuple{})を参照してください。これは接続ごとにカスタマイズできます。詳細は[`TLSConnectionOptions`](@ref)を参照してください。
