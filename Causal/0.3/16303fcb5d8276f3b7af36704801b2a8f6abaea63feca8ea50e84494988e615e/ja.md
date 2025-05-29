```julia
setlogger(path, name; setglobal, loglevel)

```

ロガーを返します。`path`はパスで、`name`はロガーのファイル名です。`setglobal`が`true`の場合、返されるロガーはグローバルロガーです。

# 例

```julia
julia> logger = setlogger(tempdir(), "mylogger", setglobal=true)
Base.CoreLogging.SimpleLogger(IOStream(<file /tmp/mylogger>), Info, Dict{Any,Int64}())
```
