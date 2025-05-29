```
query(db::Surreal; sql::String, vars::Union{Dict, Nothing}=nothing)
```

データベースに対して一連のSurrealQLステートメントを実行します。

# 引数

`sql`: SurrealQLステートメントを指定します。 `vars`: クエリで使用できる変数を割り当てます。

# 戻り値

レコード。

# 例

```jldoctest
julia> # 接続で変数を割り当てる
julia> result = query(db, sql=r"create person; select * from type::table($tb)",vars=Dict("tb"=> "person"))
julia> # 最初のクエリから最初の結果を取得する
julia> result[0]["result"][0]
julia> # 2番目のクエリからすべての結果を取得する
julia> result[1]["result"]
```
