```
Surreal(f::Function, url::String; npool=1)
```

関数 `f` を `Surreal(url, npool)` の結果に適用し、完了後にデータベースディスクリプタを閉じます。

# 例

```jldoctest
julia> Surreal("ws://localhost:8000/rpc") do db
			connect(db)
			signin(db,user="root", pass="root")
			use(db, namespace="test", database="test")
			create(db, thing="person",
					data = Dict("user"=> "me","pass"=> "safe","marketing"=> true,
								"tags"=> ["python", "documentation"]))
		end
```
