```markdown
check(resource::T) where T

タイプ `T` のリソースの有効性を確認します。

この関数は、リソース取得（`acquire!`）中にプールによって自動的に呼び出されます。`check` が失敗した場合、リソースは無効と見なされ、プールは新しいリソースを作成するか、別の空いているリソースを取得しようとします。このメソッドを実装することは、プールがユーザーに有効なリソースのみを提供することを保証するために不可欠です。

# 引数

  * `resource::T`: 検証するリソース。

# ジェネリックメソッド

何もしないジェネリック `check(::T) where T` メソッドが提供されており、これは特定の `check` メソッドをリソースタイプのために定義しない場合、すべてのリソースが有効と見なされることを意味します。これは便利に思えるかもしれませんが、リソースタイプに対して適切なチェックを行う特定の `check` メソッドを実装することを*強く推奨*します。適切な検証なしにジェネリックメソッドに依存すると、予期しないエラーやリソースリークを引き起こす可能性があります。

# 例

```

julia using Pools, Redis, Dates import Pools: create, check

struct Connection     client::RedisConnection     timestamp::DateTime end

function check(redis::Connection)     ping(redis.client) end ```
