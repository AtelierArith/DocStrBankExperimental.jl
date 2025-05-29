### abstract type AbstractUDPConnection <: Toolips.AbstractConnection

The `AbstractUDPConnection` fills the same role as the `Toolips.AbstractConnection` –  being a mutable type that is passed into a response handler. The `Connection` is then  used alongside `respond!`, `send`, and its `packet` field to create and send data to handle the  response.

  * See also: `UDPConnection`, `UDPIOConnection`, `start!`

##### consistencies

  * `ip`**::String**
  * `port`**::Int64**
  * `packet`**::String**
  * `data`**::Dict{Symbol, Any}**
