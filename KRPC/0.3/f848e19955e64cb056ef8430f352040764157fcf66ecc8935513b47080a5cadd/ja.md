```
add_stream(conn::KRPCConnection, calls::T) where {K, T<:Tuple{Vararg{RT where {S, P, R, RT<:Request{S, P, R}}, K}}}
```

指定されたコールのセットに対してリスナーを追加し、返します。返されるリスナーは、ストリームされたコールの*任意の*更新に対して結合された値を生成します。

# 例

```
using KRPC.Interface.SpaceCenter
stream = add_stream(conn, (KRPC.Interface.SpaceCenter.get_ActiveVessel(), KRPC.Interface.SpaceCenter.get_GameMode()))
for (vessel, game_mode) in stream 
    println("現在の船は$vesselで、ゲームモードは$game_modeです")
end
```
