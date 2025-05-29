```
aws_secure_tunnel_stream_reset(secure_tunnel, message_options)
```

セキュアトンネルで STREAM_RESET メッセージをキューに追加します

!!! compat "非推奨"
    この関数は使用しないでください。


# 引数

  * `secure_tunnel`: メッセージをキューに追加するためのセキュアトンネル
  * `message_options`: メッセージ操作のための設定オプション

# 戻り値

メッセージ操作を開始する同期ロジックにおける成功/失敗

### プロトタイプ

```c
int aws_secure_tunnel_stream_reset( struct aws_secure_tunnel *secure_tunnel, const struct aws_secure_tunnel_message_view *message_options);
```
