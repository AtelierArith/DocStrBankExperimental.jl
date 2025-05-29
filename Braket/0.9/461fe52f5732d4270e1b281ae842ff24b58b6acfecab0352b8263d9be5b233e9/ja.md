```
metadata(t::AwsQuantumTask, ::Val{false})
metadata(t::AwsQuantumTask, ::Val{true})
```

タスク`t`のメタデータを取得します。第二引数が`::Val{true}`の場合、利用可能な場合は以前にキャッシュされたメタデータを使用し、そうでなければBraketサービスから取得します。第二引数が`::Val{false}`（デフォルト）の場合、以前にキャッシュされたメタデータを使用せず、Braketサービスから新しいメタデータを取得します。
