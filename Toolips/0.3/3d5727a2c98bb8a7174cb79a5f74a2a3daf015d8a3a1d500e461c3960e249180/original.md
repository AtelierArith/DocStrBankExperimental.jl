```julia
route!(c::AbstractConnection, e::AbstractExtension) -> ::Nothing
```

This `route!` binding is called each time the `Connection` is created for each exported `AbstractExtension`  with a `route!` `Method`. This `Function` is designed to be imported and extended.

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
    write!(c, "you are client #" * string(c[:clients]))
end

counter = ClientCounter()
export counter, home
end
```

  * See also: `Connection`, `route!`, `on_start`, `Toolips`, `Extension`
