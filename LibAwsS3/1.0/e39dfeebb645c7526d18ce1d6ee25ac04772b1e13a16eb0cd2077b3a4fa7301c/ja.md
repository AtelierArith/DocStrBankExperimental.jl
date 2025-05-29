```
aws_s3_request_metrics_get_ip_address(metrics, out_ip_address)
```

リクエストが接続されているIPアドレスを取得します。利用できない場合、AWS*ERROR*S3*METRIC*DATA*NOT*AVAILABLEが発生します。利用可能な場合、out*ip*addressは文字列に設定されます。この文字列のライフタイムはmetricsオブジェクトに関連付けられていることに注意してください。

### プロトタイプ

```c
int aws_s3_request_metrics_get_ip_address( const struct aws_s3_request_metrics *metrics, const struct aws_string **out_ip_address);
```
