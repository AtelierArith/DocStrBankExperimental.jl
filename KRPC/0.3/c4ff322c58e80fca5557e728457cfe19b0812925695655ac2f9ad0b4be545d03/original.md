```
kerbal(c::KRPCConnection, call::Request{S, P, R}) where {S, P, R}
```

Send a single message `call` to the server with connection `c`. See the  call stubs generated in the KRPC.Interface.[service] module for valid requests.

# Examples

```
active_vessel = kerbal(conn, KRPC.Interface.SpaceCenter.get_ActiveVessel())
```
