```
aws_crt_statistics_tls_reset(stats)
```

次の収集間隔のためにtlsチャネルハンドラの統計をリセットします。計算済みの結果はそのままにされます。

### プロトタイプ

```c
void aws_crt_statistics_tls_reset(struct aws_crt_statistics_tls *stats);
```
