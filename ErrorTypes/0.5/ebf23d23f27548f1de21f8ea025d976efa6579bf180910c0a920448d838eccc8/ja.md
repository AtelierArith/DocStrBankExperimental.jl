```
ok(x::Result{T})::Option{T}
```

`Result`から`Option`を構築します。`Ok`バリアントは`some`になり、`Err`バリアントは`none(T)`になり、エラー値は存在する場合に破棄されます。

# 例

```jldoctest
julia> ok(Result{Int32, String}(Err("Some error message")))
none(Int32)

julia> ok(Result{String, Dict}(Ok("Success!")))
some("Success!")

julia> ok(some(5))
some(5)
```
