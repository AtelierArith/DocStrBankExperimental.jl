```
kerbal_connect(f::Function, client_name::String, host::String="localhost", port::Int64=50000, stream_port::Int64=50001)
```

`kerbal_connect`のDo-記法バージョンで、doブロックの終了後に自動的に接続を閉じます。

# 例

ローカルホストに「test」として接続し、デフォルトのポートを使用します：

```julia-repl
julia> kerbal_connect("test") do conn
         println("connected!")
       end
```
