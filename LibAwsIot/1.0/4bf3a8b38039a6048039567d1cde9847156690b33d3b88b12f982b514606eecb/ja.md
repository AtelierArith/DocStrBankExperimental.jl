```
aws_secure_tunnel_send_message(secure_tunnel, message_options)
```

セキュアトンネル内でメッセージ操作をキューに追加します

# 引数

  * `secure_tunnel`: メッセージをキューに追加するためのセキュアトンネル
  * `message_options`: メッセージ操作のための設定オプション

# 戻り値

メッセージ操作を開始する同期ロジックにおける成功/失敗

### プロトタイプ

```c
int aws_secure_tunnel_send_message( struct aws_secure_tunnel *secure_tunnel, const struct aws_secure_tunnel_message_view *message_options);
```
