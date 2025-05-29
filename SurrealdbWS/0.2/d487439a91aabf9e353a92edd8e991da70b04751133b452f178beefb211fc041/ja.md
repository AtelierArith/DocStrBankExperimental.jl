```
insert(db::Surreal; thing::String, data::Union{Dict, Nothing}=nothing)
```

データベースにレコードを挿入します。この関数はデータベースで次のクエリを実行します: `thing` コンテンツ `data` を挿入します。

# 引数

  * `thing`: テーブルまたはレコードID。
  * `data`: 挿入するドキュメント / レコードデータ。

# 例

```jldoctest

# ランダムIDでレコードを挿入

julia> person = insert(db, "person")

# 特定のIDでレコードを挿入

julia> record = insert(db,"person:tobie", Dict( 	"name"=> "Tobie", 	"settings"=> Dict( 		"active"=> true, 		"marketing"=> true, 		), 	)
```
