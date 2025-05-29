```julia
get_route(c::AbstractConnection) -> ::String
```

現在のターゲットを取得します。`Connection`の受信。 (この`Function`は、ルーターが受信接続をあなたのルートに誘導するために使用されます。)

```example
module MyServer
using Toolips
using Test

logger = Toolips.Logger()

home = route("/") do c::Connection
    @test get_route(c) == "/"
end

export home, logger
end
```
