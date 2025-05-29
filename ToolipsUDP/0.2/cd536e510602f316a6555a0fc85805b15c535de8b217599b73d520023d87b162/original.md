```julia
UDPConnection <: AbstractUDPConnection
```

  * ip**::String**
  * port**::Int64**
  * packet**::String**
  * data**::Dict{Symbol, Any}**
  * server**::Sockets.UDPSocket**

---

The `UDPConnection` is passed into your `UDPHandler`'s function. This is essentially the in and out stream  in `ToolipsUDP`. We respond using `send` and `respond!` and we get the incoming packet by calling the  `c.packet` field.

##### constructors

  * `UDPConnection(data::Dict{Symbol, Any}, server::Sockets.UDPSocket)`
