```
use(db::Surreal; namespace::String, database::String)
```

特定の名前空間とデータベースに切り替えます。

# 引数

  * `namespace`: 特定の名前空間に切り替えます。
  * `database`: 特定のデータベースに切り替えます。

# 例

```jldoctest
julia> use(db, namespace='test', database='test')
```
