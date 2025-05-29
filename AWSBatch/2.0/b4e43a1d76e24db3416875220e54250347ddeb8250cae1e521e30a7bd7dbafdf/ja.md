```
create_compute_environment(name;
                           managed=true,
                           role="",
                           resources=Dict(),
                           enabled=true,
                           tags=Dict(),
                           aws_config=global_aws_config())
```

`name`という名前の`type`タイプの計算環境を作成します。

AWSのドキュメントは[こちら](https://docs.aws.amazon.com/batch/latest/APIReference/API_CreateComputeEnvironment.html)を参照してください。
