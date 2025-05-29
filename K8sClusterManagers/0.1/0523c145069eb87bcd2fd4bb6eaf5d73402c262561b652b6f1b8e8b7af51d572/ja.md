```
K8sClusterManager(np::Integer; kwargs...)
```

Kubernetes (k8s) を使用したクラスター マネージャーで、追加のポッドをワーカーとしてスピンアップします。`np` ワーカーをスピンアップしようとしますが、クラスターに利用可能なリソースが少ない場合は、少ないワーカーで起動することがあります。

## 引数

  * `np`: 起動するワーカーポッドの希望数。

## キーワード

  * `namespace`: ワーカーポッドを起動する Kubernetes ネームスペース。デフォルトは `current_namespace()` です。
  * `manager_pod_name`: マネージャーポッドの名前。デフォルトは `gethostname()` で、Kubernetes ポッド内で実行されるときのポッドの名前です。
  * `worker_prefix`: スピンアップされたワーカーに付けられるプレフィックス。マネージャーが K8s 内で実行されている場合はデフォルトで `"$(manager_pod_name)-worker"` になり、それ以外の場合は `"witch-worker"` になります。
  * `image`: ワーカーに使用する Docker イメージ。マネージャーが K8s ポッド内で実行されているときに使用されるイメージがデフォルトで、それ以外の場合は "julia::VERSION" になります。
  * `cpu`: 各ワーカーに要求される [CPU リソース](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/#meaning-of-cpu)。デフォルトは `1` です。
  * `memory`: 各ワーカーに要求される [メモリリソース](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/#meaning-of-memory) バイト単位。リクエストには単位のサフィックスを提供できます（例: "G" はギガバイト、"Gi" はギビバイト）。デフォルトは `"4Gi"` です。
  * `pending_timeout`: "Pending" ワーカーポッドが "Running" フェーズに入るまで待機する最大秒数。タイムアウトに達すると、マネージャーは利用可能なワーカーの数 (`<= np`) で続行します。デフォルトは `180` (3 分) です。
  * `configure`: ワーカーポッドの仕様を作成前に変更できる関数。デフォルトは `identity` です。
