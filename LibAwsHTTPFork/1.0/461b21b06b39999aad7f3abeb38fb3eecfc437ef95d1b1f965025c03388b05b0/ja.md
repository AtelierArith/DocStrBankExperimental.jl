```
aws_http_proxy_new_socket_channel(channel_options, proxy_options)
```

HTTPプロキシを介してCONNECTトンネリングを通じて任意のプロトコル接続を確立します。この接続プロセスが成功するためにALPNは必須ではありませんが、利用可能な場合は使用を推奨します。

# 引数

  * `channel_options`: ソケットレベル接続のための設定オプション
  * `proxy_options`: プロキシ接続のための設定オプション

# 戻り値

非同期チャネルの開始が成功した場合はAWS*OP*SUCCESS、そうでない場合はAWS*OP*ERR

### プロトタイプ

```c
int aws_http_proxy_new_socket_channel( struct aws_socket_channel_bootstrap_options *channel_options, const struct aws_http_proxy_options *proxy_options);
```
