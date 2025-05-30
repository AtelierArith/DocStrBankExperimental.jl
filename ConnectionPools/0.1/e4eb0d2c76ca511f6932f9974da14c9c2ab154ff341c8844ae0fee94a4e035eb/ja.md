clean!(resource::T) where T

タイプ `T` のリソースに関連付けられたリソースをクリーンアップします。

この関数は、次の状況でプールによって自動的に呼び出されます：

  * リソースが検証に失敗したとき（`check` 関数によって判断されます）。
  * リソースがプールから削除されたとき（例：プールの排水中やプールの制限が減少したとき）。

リソースが保持している外部リソースを解放するために、このメソッドを実装する必要があります（例：接続を閉じる、メモリを解放するなど）。このメソッドを実装しない場合、デフォルトの実装は何もしません。

# 引数

  * `resource::T`: クリーンアップするリソース。

# ジェネリックメソッド

何もしないジェネリック `clean!(::T) where T` メソッドが提供されています。リソースにクリーンアップが必要な場合は、特定の `clean!` メソッドを実装することを*強く推奨*します。

# 例

```julia
using Pools, Redis, Dates
import Pools: create, clean!

struct Connection
    client::RedisConnection
    timestamp::DateTime
end

function clean!(redis::Connection)
    Redis.disconnect(redis.client)
end
```
