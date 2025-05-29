```
create_job_queue(name, envs, priority=1; aws_config=global_aws_config())
```

名前 `name` と優先度 `priority` のジョブキューを作成し、関連する `JobQueue` オブジェクトを返します。 `envs` は ARN によって与えられるコンピュート環境のイテレータでなければなりません。

AWS ドキュメントは [こちら](https://docs.aws.amazon.com/batch/latest/APIReference/API_CreateJobQueue.html) をご覧ください。
