```
aws_secure_tunnel_stop(secure_tunnel)
```

非同期でセキュアトンネルに停止状態に遷移するよう通知します。セキュアトンネルが停止状態に達すると、すべてのセッション状態が消去されます。

# 引数

  * `secure_tunnel`: 停止するセキュアトンネル

# 戻り値

開始プロセスを開始する同期ロジックにおける成功/失敗

### プロトタイプ

```c
int aws_secure_tunnel_stop(struct aws_secure_tunnel *secure_tunnel);
```
