drain!(pool::Pool{T}) where T

リソースプールを排出し、すべてのリソースを解放および最終化します。

この関数は、プールによって現在保持されているすべてのリソース（自由なものと取得されたものの両方）を解放します。取得されたすべてのリソースがプールに戻されるのを待ってから、それらを最終化します。これは通常、プールをシャットダウンしたいときや、すべてのリソースが適切にクリーンアップされることを確認する必要があるときに使用されます。

# 引数

  * `pool::Pool{T}`: 排出するリソースプール。

# スレッド安全性

この操作はスレッドセーフです。

# 例

```julia
using Redis, Dates

struct Connection
    client::RedisConnection
    timestamp::DateTime
end

create(::Type{Connection}) = Connection(RedisConnection(host = "localhost", port = 6379, db = 3), now())
clean!(redis::Connection) = Redis.disconnect(redis.client)

pool = ConnectionPool{Connection}(3)

withresource(pool) do redis
    ping(redis.client)
end

drain!(pool)
```
