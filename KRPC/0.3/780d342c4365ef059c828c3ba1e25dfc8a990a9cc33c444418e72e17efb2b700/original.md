```
add_stream(f::Function, conn::KRPCConnection, calls::T) where {K, T<:Tuple{Vararg{RT where {S, P, R, RT<:Request{S, P, R}}, K}}}
```

# Examples

Do-notation version of add_stream.

```
add_stream(conn, (KRPC.Interface.SpaceCenter.get_ActiveVessel(), KRPC.Interface.SpaceCenter.get_GameMode())) do stream
    nmessages = 0
    for (vessel, game_mode) in stream 
        println("The current vessel is $vessel in game mode $game_mode")
    end
end
```
