```
state(t::AwsQuantumTask, ::Val{false}) -> String
state(t::AwsQuantumTask, ::Val{true}) -> String
state(t::AwsQuantumTask) -> String
```

タスク`t`の状態を取得します。可能な状態は`"CANCELLED"`、`"FAILED"`、`"COMPLETED"`、`"QUEUED"`、および`"RUNNING"`です。第二引数が`::Val{true}`の場合、利用可能であれば以前にキャッシュされたメタデータを使用し、そうでなければBraketサービスから取得します。第二引数が`::Val{false}`（デフォルト）の場合、以前にキャッシュされたメタデータを使用せず、Braketサービスから新しいメタデータを取得します。
