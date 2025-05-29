```
add_stream(f::Function, conn::KRPCConnection, calls::T) where {K, T<:Tuple{Vararg{RT where {S, P, R, RT<:Request{S, P, R}}, K}}}
```

# 例

add_streamのDo-記法バージョン。

```
add_stream(conn, (KRPC.Interface.SpaceCenter.get_ActiveVessel(), KRPC.Interface.SpaceCenter.get_GameMode())) do stream
    nmessages = 0
    for (vessel, game_mode) in stream 
        println("現在の船は$ vesselで、ゲームモードは$ game_modeです")
    end
end
```
