```
Surreal(f::Function, url::String; npool=1)
```

Apply the function `f` to the result of `Surreal(url, npool)` and close the db descriptor upon completion.

# Examples

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
