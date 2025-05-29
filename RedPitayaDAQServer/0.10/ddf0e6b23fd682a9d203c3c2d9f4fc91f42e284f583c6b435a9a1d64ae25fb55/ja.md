```
serverMode!(rp::RedPitaya, mode::ServerMode)
```

サーバーのモードを設定します。有効な値は "`CONFIGURATION`" と "`ACQUISITION`" です。

# 例

```julia
julia> serverMode!(rp, ACQUISITION);
true

julia> serverMode(rp)
ACQUISITION
```
