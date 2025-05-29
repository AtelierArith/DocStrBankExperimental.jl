```
aws_secure_tunnel_stream_start(secure_tunnel, message_options)
```

セキュアトンネル内でSTREAM_STARTメッセージをキューします

!!! note
    この関数はソースモードからのみ使用するべきです。


# 引数

  * `secure_tunnel`: メッセージをキューするためのセキュアトンネル
  * `message_options`: メッセージ操作のための設定オプション

# 戻り値

メッセージ操作を開始する同期ロジックにおける成功/失敗

### プロトタイプ

```c
int aws_secure_tunnel_stream_start( struct aws_secure_tunnel *secure_tunnel, const struct aws_secure_tunnel_message_view *message_options);
```
