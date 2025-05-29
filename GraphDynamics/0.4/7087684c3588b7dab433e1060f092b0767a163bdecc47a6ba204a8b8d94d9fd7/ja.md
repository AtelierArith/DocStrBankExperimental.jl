```
ForeachConnectedSubsystem
```

これは、関数を受け取り、その関数を以前に指定されたサブシステムからの接続を持つ各サブシステムに対して呼び出す呼び出し可能な構造体です。

つまり、次のように書くことは

```julia
F = ForeachConnectedSubsystem{k}(l, states_partitioned, params_partitioned, connection_matrices)

F() do conn, sys_dst, states_view_dst, params_view_dst
    [...]
end
```

は、次のように書くことの型安定版のようなものです。

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
                [...] # <------- ユーザーコードここに
            ends
        end
    end
end
```
