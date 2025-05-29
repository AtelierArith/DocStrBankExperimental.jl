```julia
respond!(c::AbstractUDPConnection, data::String) -> ::Nothing
```

クライアントにデータを返すための本質的な方法; `respond!` は従来の `Toolips` における `write!` の代わりを務め、受信したパケットにデータを直接書き込むことを可能にします。

```julia
module HelloWorld
using ToolipsUDP


main_handler = handler() do c::UDPConnection
    respond!(c, "hello world!")
end

export main_handler
end

# マルチハンドラーには、メインハンドラーを自動的に作成するために `Function` を渡すこともできます。
multi_handler = MultiHandler() do c::AbstractUDPConnection

end
```
