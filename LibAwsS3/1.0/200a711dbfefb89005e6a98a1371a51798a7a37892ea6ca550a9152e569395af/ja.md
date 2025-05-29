```
aws_s3_request_metrics_get_host_address(metrics, out_host_address)
```

リクエストのhost*addressを取得します。利用できない場合、AWS*ERROR*S3*METRIC*DATA*NOT*AVAILABLEが発生します。利用可能な場合、out*host_addressは文字列に設定されます。この文字列のライフタイムはmetricsオブジェクトに関連付けられていることに注意してください。

### プロトタイプ

```c
void aws_s3_request_metrics_get_host_address( const struct aws_s3_request_metrics *metrics, const struct aws_string **out_host_address);
```
