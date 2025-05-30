```markdown
change!(resource::T) where T

リソースの状態を、再利用される前にタイプ `T` のリソースで変更します。

この関数は、リソースが `release!` を介してプールに返されるときにプールによって自動的に呼び出されます。これにより、接続パラメータのリセット、タイムスタンプの変更など、リソースの内部状態を更新する機会が提供されます。

リソースが再利用される前に状態変更を必要とする場合は、このメソッドを実装する*べき*です。更新が必要ない場合は、このメソッドを未実装のままにしておくことができ、デフォルトの実装は何もしません。

# 引数

  * `resource::T`: 修正するリソース。

# ジェネリックメソッド

何もしないジェネリック `change!(::T) where T` メソッドが提供されます。これは、リソースタイプの特定の `change!` メソッドを定義しない場合のデフォルト実装として機能します。ただし、リソースが状態変更を必要とする場合は、特定の `change!` メソッドを実装することを*強く推奨*します。

# 例

```

julia using Pools, Redis, Dates import Pools: create, change!

mutable struct Connection     client::RedisConnection     timestamp::DateTime end

function change!(redis::Connection)     redis.timestamp = now() end ```
