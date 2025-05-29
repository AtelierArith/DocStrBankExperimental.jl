```
serverMode(rp::RedPitaya)
```

サーバーのモードを返します。

# 例

```julia
julia> serverMode!(rp, ACQUISITION);
true

julia> serverMode(rp)
ACQUISITION
```
