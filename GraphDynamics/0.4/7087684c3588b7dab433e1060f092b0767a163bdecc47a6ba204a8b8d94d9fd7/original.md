```
ForeachConnectedSubsystem
```

This is a callable struct which takes in a function, and then calls that function on each subsystem which has a connection leading to it from some previously specified subsystem.

That is, writing

```julia
F = ForeachConnectedSubsystem{k}(l, states_partitioned, params_partitioned, connection_matrices)

F() do conn, sys_dst, states_view_dst, params_view_dst
    [...]
end
```

is like a type stable version of writing

```
for i in eachindex(states_partitioned)
    for nc in eachindex(connection_matrices)
        M = connection_matrices[nc][i, k]
        for j in eachindex(states_partitioned[k])
            conn = M[l, j]
            if !iszero(conn)
                states_view_dst = @view states_partitioned[i][j]
                params_view_dst = @view params_partitioned[i][j]
                sys_dst = Subsystem(states_view_dst[], params_view_dst[])
                [...] # <------- User code here
            ends
        end
    end
end
```
