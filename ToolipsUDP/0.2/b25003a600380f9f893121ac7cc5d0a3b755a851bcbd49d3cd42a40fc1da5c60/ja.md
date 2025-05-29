```julia
UDPExtension{T <: Any} <: AbstractUDPExtension
```

これは、"クイック拡張"のためにパラメトリックに使用される空の`UDPExtension`です。例えば、`UDPExtension{:cr}`のための`on_start`ディスパッチを書き、サーバーにデータをロードするために`UDPExtension{:cr}`をエクスポートすることができます。

```julia
module NewServer
using ToolipsUDP
import ToolipsUDP: on_start, route!, UDPExtension

# 各レスポンスで呼び出される
function route!(c::UDPConnection, ext::UDPExtension{:cr})

end

# サーバーが起動したときに呼び出される
function on_start(data:::Dict{Symbol, Any}, ext::UDPExtension{:cr})
    push!(data, :count => 5)
end

mainhandler = handler("counter") do c::UDPConnection
    c[:count] += 5
end

data_ext = UDPExtension{:cr}()
export mainhandler, data_ext
end
```

  * 参照: `handler`, `UDPConnection`, `on_start`, `route!`, `AbstractUDPExtension`

```julia
UDPExtension{T <: Any}()
```
