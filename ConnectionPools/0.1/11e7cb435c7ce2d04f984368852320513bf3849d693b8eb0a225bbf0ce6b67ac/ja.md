```markdown
release!(pool::Pool{T}, resource::T)

リソースをプールに戻します。

この関数はリソースをプールに戻し、再利用可能にします。リソースの状態を変更し（`change!`関数を使用）、リソースが利用可能になったことを待機中のタスクに通知します。

# 引数

  * `pool::Pool{T}`: リソースを戻すプール。
  * `resource::T`: 戻すリソース。

# 例外

  * `ArgumentError`: 提供された`resource`がプールに属していない場合（つまり、このプールから取得されていない場合）。
  * `change!(resource::T)`関数によってスローされる例外。

# スレッドセーフ

この操作はスレッドセーフです。

# 例

```

julia using Redis, Dates

struct Connection     client::RedisConnection     timestamp::DateTime end

create(::Type{Connection}) = Connection(RedisConnection(host = "localhost", port = 6379, db = 3), now()) change!(redis::Connection) = redis.timestamp = now()

pool = ConnectionPool{Connection}(3) conn = acquire!(pool) release!(pool, conn)

```

```
