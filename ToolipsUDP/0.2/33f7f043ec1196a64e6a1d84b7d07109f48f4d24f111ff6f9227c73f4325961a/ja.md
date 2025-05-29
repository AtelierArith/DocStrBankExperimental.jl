```julia
get_ip4(c::UDPConnection) -> ::Toolips.IP4
```

`Toolips.IP4`データ型の`get_ip`に相当するもので、ポートとIPアドレスの両方を保持します。これは、`Toolips` HTTPサーバーが本番環境で使用するポートが常に80であるため、`ToolipsUDP`によってのみ提供されます。これは非常に特異なケースを除いてです。

```julia
    default_handler = handler() do c::UDPConnection
    println("クライアントにサービスを提供しました")
    respond!(c, "こんにちは、世界！")
end
```
