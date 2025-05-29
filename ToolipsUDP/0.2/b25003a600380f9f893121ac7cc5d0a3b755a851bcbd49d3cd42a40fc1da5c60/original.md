```julia
UDPExtension{T <: Any} <: AbstractUDPExtension
```

This is a blank `UDPExtension` to be used parametrically with multiple  dispatch for " quick extensions". For example, we could write an `on_start` dispatch      for a `UDPExtension{:cr}` and export a `UDPExtension{:cr}` to load some data into the server.

```julia
module NewServer
using ToolipsUDP
import ToolipsUDP: on_start, route!, UDPExtension

# called on each response
function route!(c::UDPConnection, ext::UDPExtension{:cr})

end

# called when the server starts
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

  * See also: `handler`, `UDPConnection`, `on_start`, `route!`, `AbstractUDPExtension`

```julia
UDPExtension{T <: Any}()
```
