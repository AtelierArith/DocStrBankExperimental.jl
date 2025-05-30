```markdown
GenericPool{T}(limit::Int)

スレッドセーフなリソースプールマネージャーで、型 `T` のリソースを管理します。

この構造体はリソースプールを実装しており、最大同時実行制限を持つリソースの取得と解放を管理します。データベース接続や効率的に管理・再利用する必要がある他のオブジェクトなど、さまざまなリソースタイプで使用することを目的としています。

# 型パラメータ

  * `T`: プールによって管理されるリソースの型。

# フィールド

  * `limit::Int`: 同時に使用できるリソースの最大数。
  * `free::Vector{T}`: プール内で現在利用可能（空き）のリソースを含むベクター。
  * `taken::Set{T}`: 現在ユーザーによって使用中（取得済み）のリソースを含むセット。
  * `lock::ReentrantLock`: スレッドセーフのために使用される再入可能ロック。プールに対するすべての操作はこのロックによって保護されています。
  * `condition::Threads.Condition`: リソースが利用可能になると待機中のタスクに通知するために使用される条件変数。

# コンストラクタ

```

julia GenericPool{T}(limit::Int) where T 型 T のリソース用の新しいリソースプールを、最大同時実行制限 limit で作成します。

# 引数

limit::Int: プールに許可されるリソースの最大数。正の整数でなければなりません。

# 例外

ArgumentError: limit が正の整数でない場合。

# 例

```

julia using Pools, Redis, Dates

struct Connection     client::RedisConnection     timestamp::DateTime end

pool = GenericPool{Connection}(3) ```
```
