```
xrootd(f::Function; adjust_PATH::Bool=true, adjust_LIBPATH::Bool=true)
```

xrootdの実行をサポートする`ExecutableProduct`ラッパーです。

!!! warning "非推奨"
    このメソッドはスレッドセーフではないため非推奨であり、将来のJuliaバージョンで削除されます。代わりに非doブロック形式を使用してください。


# 例

```julia
xrootd() do exe
    run(`$exe $arguments`)
end
```

!!! compat "Julia 1.3"
    このメソッドはJuliaバージョン1.3以降を必要とします。

