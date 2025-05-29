```
aws_s3_request_metrics_get_request_id(metrics, out_request_id)
```

*********************************** S3リクエストメトリクスのゲッター ***********************************************

[`aws_s3_request_metrics`](@ref)からリクエストIDを取得します。利用できない場合、AWS*ERROR*S3*METRIC*DATA*NOT*AVAILABLEが発生します。利用可能な場合、out*request*idは文字列に設定されます。この文字列のライフタイムはメトリクスオブジェクトに関連付けられていることに注意してください。

### プロトタイプ

```c
int aws_s3_request_metrics_get_request_id( const struct aws_s3_request_metrics *metrics, const struct aws_string **out_request_id);
```
