```
kerbal(c::KRPCConnection, calls::T) where {K, T<:Tuple{Vararg{RT where {S, P, R, RT<:Request{S, P, R}}, K}}}
```

Send multiple messages `calls` to the server with connection `c`. See the  call stubs generated in the KRPC.Interface.[service] module for valid requests.

# Examples

```
active_vessel, gamemode = kerbal(conn, (KRPC.Interface.SpaceCenter.get_ActiveVessel(), KRPC.Interface.SpaceCenter.get_GameMode()))
```
