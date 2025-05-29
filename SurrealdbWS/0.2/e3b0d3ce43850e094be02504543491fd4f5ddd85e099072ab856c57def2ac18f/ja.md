```
select(db::Surreal; thing::String)
```

データベース内のテーブル（または他のエンティティ）からすべてのレコード、または特定のレコードを選択します。この関数はデータベース内で次のクエリを実行します: select * from `thing`

# 引数

```
`thing`: 選択するテーブルまたはレコードのID。
```

# 戻り値:

```
レコード。
```

# 例

```jldoctest
# テーブル（または他のエンティティ）からすべてのレコードを選択
julia> people = select(db, "person")
# テーブル（または他のエンティティ）から特定のレコードを選択
julia> person = select(db, "person:h5wxrf2ewk8xjxosxtyc")
```
