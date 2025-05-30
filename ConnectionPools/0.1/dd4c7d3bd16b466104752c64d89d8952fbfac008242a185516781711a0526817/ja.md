create(::Type{T}) where T -> T

タイプ `T` の新しいインスタンスを作成します。

この関数は、新しいリソースが必要なとき（例えば、リソースが取得され、プールが空であるか、その制限を下回っているとき）にプールによって自動的に呼び出されます。 `Pool` に格納したい任意のタイプ `T` に対して、このメソッドを *必ず* 実装する必要があります。

# 引数

  * `::Type{T}`: 作成するリソースのタイプ。このタイプはタイプパラメータであり、タイプのインスタンスではありません。

# 戻り値

タイプ `T` の新しいリソース。

# 例外

  * `MethodError`: この関数が指定されたタイプ `T` に対して実装されていない場合。

# 例

```julia

using Pools, Redis, Dates
import Pools: create

struct Connection
    client::RedisConnection
    timestamp::DateTime
end

create(::Type{Connection}) = Connection(RedisConnection(host = "localhost", port = 6379, db = 3), now())
```
