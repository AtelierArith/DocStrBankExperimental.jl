```
job_query_by_id(id::Integer)
```

キュー内の `job.id` でジョブを検索します。

見つかった場合は `job::Job` を返し、見つからなかった場合は `nothing` を返します。
