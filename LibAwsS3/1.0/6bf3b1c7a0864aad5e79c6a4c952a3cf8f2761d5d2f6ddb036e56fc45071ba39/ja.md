```
aws_s3_request_metrics_get_operation_name(metrics, out_operation_name)
```

リクエストのS3操作名を取得します（例："HeadObject"）。利用できない場合、AWS*ERROR*S3*METRIC*DATA*NOT*AVAILABLEが発生します。利用可能な場合、out*operation*nameは文字列に設定されます。この文字列のライフタイムはmetricsオブジェクトに関連付けられていることに注意してください。

### プロトタイプ

```c
int aws_s3_request_metrics_get_operation_name( const struct aws_s3_request_metrics *metrics, const struct aws_string **out_operation_name);
```
