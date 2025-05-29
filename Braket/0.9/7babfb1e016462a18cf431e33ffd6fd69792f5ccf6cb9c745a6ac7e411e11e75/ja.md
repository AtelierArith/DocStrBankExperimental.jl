```
state(j::AwsQuantumJob, ::Val{true})
state(j::AwsQuantumJob, ::Val{false})
state(j::AwsQuantumJob)
```

ジョブ `j` の状態を取得します。可能な状態は `"CANCELLED"`、`"FAILED"`、`"COMPLETED"`、`"QUEUED"`、および `"RUNNING"` です。第二引数が `::Val{true}` の場合、利用可能であれば以前にキャッシュされたメタデータを使用し、そうでなければ Braket サービスから取得します。第二引数が `::Val{false}`（デフォルト）の場合、以前にキャッシュされたメタデータを使用せず、Braket サービスから新しいメタデータを取得します。
