```
aws_secure_tunnel_start(secure_tunnel)
```

非同期でセキュアトンネルに接続を試みるよう通知します。セキュアトンネルは接続を維持しようとします。

# 引数

  * `secure_tunnel`: 開始するセキュアトンネル

# 戻り値

開始プロセスを開始する同期ロジックにおける成功/失敗

### プロトタイプ

```c
int aws_secure_tunnel_start(struct aws_secure_tunnel *secure_tunnel);
```
