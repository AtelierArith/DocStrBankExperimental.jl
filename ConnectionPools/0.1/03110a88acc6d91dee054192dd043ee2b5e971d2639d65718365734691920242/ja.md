acquire!(pool::Pool{T}) where T -> T

プールからリソースを取得します。

この関数はプールからリソースを取得しようとします。利用可能な有効なキャッシュリソースを再利用し、プールが制限を下回っている場合は新しいリソースを作成し、プールが制限に達していて有効なキャッシュリソースが利用できない場合は、リソースが利用可能になるまでブロックします。

# 引数

  * `pool::Pool{T}`: 取得するリソースプール。

# 戻り値

タイプ `T` のリソース。

# 例外

  * `MethodError`: リソースタイプ `T` に対して `create(::Type{T})` 関数が実装されていない場合。この関数は、必要に応じて新しいリソースを作成するために `Pool` にとって不可欠です。詳細については `create` のドキュメントを参照してください。
  * `check(resource::T)` 関数によってスローされる例外。`check` が例外をスローした場合、そのリソースは無効と見なされ、破棄されます。

# スレッドセーフ

この操作はスレッドセーフです。

# 例

```julia
using Redis, Dates

struct Connection
    client::RedisConnection
    timestamp::DateTime
end

create(::Type{Connection}) = Connection(RedisConnection(host = "localhost", port = 6379, db = 3), now())
check(redis::Connection) = ping(redis.client)

pool = ConnectionPool{Connection}(3)
conn = acquire!(pool)
```
