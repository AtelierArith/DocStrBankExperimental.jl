```
create(db::Surreal; thing::String, data::Union{Dict, Nothing}=nothing)
```

データベースにレコードを作成します。この関数はデータベースで次のクエリを実行します: create `thing` content `data`

# 引数

  * `thing`: テーブルまたはレコードID。
  * `data`: 挿入するドキュメント / レコードデータ。

# 例

```jldoctest

# ランダムIDでレコードを作成

julia> person = create(db, "person")

# 特定のIDでレコードを作成

julia> record = create(db,"person:tobie", Dict( 	"name"=> "Tobie", 	"settings"=> Dict( 		"active"=> true, 		"marketing"=> true, 		), 	)
```
