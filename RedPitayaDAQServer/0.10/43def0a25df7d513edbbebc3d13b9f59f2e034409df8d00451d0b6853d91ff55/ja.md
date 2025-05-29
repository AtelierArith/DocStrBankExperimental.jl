```
serverMode!(rp::RedPitaya, mode::ServerMode)
```

サーバーのモードを設定します。

# 例

```julia
julia> serverMode!(rp, ACQUISITION);
true

julia> serverMode(rp)
ACQUISITION
```
