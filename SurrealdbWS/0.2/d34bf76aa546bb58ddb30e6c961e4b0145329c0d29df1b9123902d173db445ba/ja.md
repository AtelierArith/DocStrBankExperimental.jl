```
update(db::Surreal; thing::String, data::Union{Dict, Nothing}=nothing)
```

データベース内のテーブルのすべてのレコード、または特定のレコードを更新します。この関数は、現在のドキュメント/レコードデータを指定されたデータで置き換えます。この関数は、データベース内で次のクエリを実行します: update `thing` content `data`

# 引数

  * `thing`: テーブルまたはレコードID。
  * `data`: 挿入するドキュメント/レコードデータ。

# 例:

```jldoctest
julia> # テーブル内のすべてのレコードを更新
julia> person = update(db, "person")
julia> # 特定のIDを持つレコードを更新
julia> record = update(db, "person:tobie", Dict(
	"name"=> "Tobie",
	"settings"=> Dict(
	"active"=> true,
	"marketing"=> true,
	),
	))
```
