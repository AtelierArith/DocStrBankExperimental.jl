```
metadata(j::AwsQuantumJob, ::Val{true})
metadata(j::AwsQuantumJob, ::Val{false})
metadata(j::AwsQuantumJob)
```

ジョブ `j` のメタデータを取得します。第二引数が `::Val{true}` の場合、利用可能な場合は以前にキャッシュされたメタデータを使用し、そうでない場合は Braket サービスから取得します。第二引数が `::Val{false}` （デフォルト）の場合、以前にキャッシュされたメタデータを使用せず、Braket サービスから新しいメタデータを取得します。
