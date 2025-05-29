```
xrdfs(; adjust_PATH::Bool=true, adjust_LIBPATH::Bool=true) -> Cmd
```

xrdfsを実行するための`ExecutableProduct`ラッパーです。このラッパーはスレッドセーフであり、Julia 1.6以降ではこちらを使用することが推奨されます。

# 例

```julia
run(`$(xrdfs()) $arguments`)
```

!!! compat "Julia 1.6"
    このメソッドはJuliaバージョン1.6以降を必要とします。

