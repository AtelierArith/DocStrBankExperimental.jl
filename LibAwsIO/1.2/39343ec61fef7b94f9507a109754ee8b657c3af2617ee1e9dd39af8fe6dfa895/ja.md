```
aws_crt_statistics_socket_reset(stats)
```

ソケットチャネルハンドラの統計を次の収集インターバルのためにリセットします。計算済みの結果はそのままにされます。

### プロトタイプ

```c
void aws_crt_statistics_socket_reset(struct aws_crt_statistics_socket *stats);
```
