```
add_stream(conn::KRPCConnection, calls::T) where {K, T<:Tuple{Vararg{RT where {S, P, R, RT<:Request{S, P, R}}, K}}}
```

Add and return a listener for a given set of calls to KRPC. The returned listener will produce a combined value for *any* update of the streamed calls.

# Examples

```
using KRPC.Interface.SpaceCenter
stream = add_stream(conn, (KRPC.Interface.SpaceCenter.get_ActiveVessel(), KRPC.Interface.SpaceCenter.get_GameMode()))
for (vessel, game_mode) in stream 
    println("The current vessel is $vessel in game mode $game_mode")
end
```
