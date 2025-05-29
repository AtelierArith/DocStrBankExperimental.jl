```
ElasticManager <: Distributed.ClusterManager
```

動的にワーカーを追加および削除することを可能にするクラスターマネージャーです。

コンストラクタ:

```julia
function ElasticManager(;
    addr=IPv4("127.0.0.1"), port=9009, cookie=nothing,
    topology=:all_to_all, manage_callback=elastic_no_op_callback
)
```

マネージャーは `addr:port` でワーカー接続を待ち受けます。ワーカーは `cookie`（デフォルトではランダムに生成される）で自分自身を認証する必要があります。`topology` はJuliaクラスタートポロジーを設定し、`:all_to_all` または `:master_worker` である可能性があります（詳細は `Distributed.addprocs` のドキュメントを参照してください）。

ワーカーは `Distributed.addprocs` を介して追加されるのではなく、外部のJuliaプロセスから [`ElasticClusterManager.elastic_worker`](@ref) を介して開始されます。これはユーザーに委ねられています。

`manage_callback` がユーザー提供の `my_manage_callback` に設定されている場合、`Distributed.manage` が弾力的なワーカーを追加または削除する際に、プライマリのJuliaプロセスで呼び出されます。コールバックのシグネチャは次のとおりです。

```julia
my_manage_callback(mgr::ElasticManager, id::Integer, :register)
my_manage_callback(mgr::ElasticManager, id::Integer, :deregister)
```

これを使用して、`Distributed.WorkerPool` にワーカーを自動的に追加することができます。
