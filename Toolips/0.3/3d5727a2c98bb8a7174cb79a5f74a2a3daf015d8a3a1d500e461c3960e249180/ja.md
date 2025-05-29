```julia
route!(c::AbstractConnection, e::AbstractExtension) -> ::Nothing
```

この `route!` バインディングは、各 `AbstractExtension` に対して `Connection` が作成されるたびに呼び出されます。これは `route!` メソッドを持つものです。この `Function` はインポートされ、拡張されることを目的としています。

```julia
module ClientCount
using Toolips
import Toolips: route!, on_start

mutable struct ClientCounter <: Toolips.AbstractExtension

end

function on_start(ext::ClientCounter, data::Dict{Symbol, Any}, routes::Vector{<:AbstractRoute})
    push!(data, :clients => 0)
end

function route!(c::AbstractConnection, e::ClientCounter)
    c[:clients] += 1
end

home = route("/") do c::Connection
    write!(c, "あなたはクライアント #" * string(c[:clients]))
end

counter = ClientCounter()
export counter, home
end
```

  * 参照: `Connection`, `route!`, `on_start`, `Toolips`, `Extension`
