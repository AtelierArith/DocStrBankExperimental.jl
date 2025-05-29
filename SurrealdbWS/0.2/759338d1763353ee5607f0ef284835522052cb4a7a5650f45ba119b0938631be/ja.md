```
merge(db::Surreal; thing::String, data::Union{AbstractDict, Nothing}=nothing)

merge(db::Surreal; thing::String, data::Union{Dict, Nothing}=nothing)
```

データベースにレコードをマージします。この関数はデータベース内で次のクエリを実行します: merge `thing` コンテンツ `data`

# 引数

  * `thing`: テーブルまたはレコードID。
  * `data`: マージするドキュメント / レコードデータ。

# 例

```jldoctest

# ランダムIDでレコードをマージ

julia> person = merge(db, "person")

# 特定のIDでレコードをマージ

julia> record = merge(db,"person:tobie", Dict( 	"name"=> "Tobie", 	"settings"=> Dict( 		"active"=> true, 		"marketing"=> true, 		), 	)
```
