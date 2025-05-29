```
subscribe(uri::URI)
```

This is the general version of websocket subscription that the other exchange-specific versions of subscribe are built on.  It connects to the given uri and returns a struct that contains two Channels that can be used to interact with the WebSocket.

# Example

```julia-repl
julia> using URIs, JSON3

julia> s = subscribe(URI("wss://ws.bitstamp.net"))
CryptoMarketData.Session(URI("wss://ws.bitstamp.net"), missing, missing, missing, Task (runnable) @0x00007970dac63d00)

julia> btcusd_subscribe = Dict(:event => "bts:subscribe", :data => Dict(:channel => "live_trades_btcusd"))
Dict{Symbol, Any} with 2 entries:
  :event => "bts:subscribe"
  :data  => Dict(:channel=>"live_trades_btcusd")

julia> put!(s.commands, JSON3.write(btcusd_subscribe))
"{"event":"bts:subscribe","data":{"channel":"live_trades_btcusd"}}"

julia> s.messages
Channel{Any}(32) (2 items available)

julia> take!(s.messages)
"{"event":"bts:subscription_succeeded","channel":"live_trades_btcusd","data":{}}"

julia> JSON3.read(take!(s.messages))
JSON3.Object{Base.CodeUnits{UInt8, String}, Vector{UInt64}} with 3 entries:
  :data    => {…
  :channel => "live_trades_btcusd"
  :event   => "trade"
```
