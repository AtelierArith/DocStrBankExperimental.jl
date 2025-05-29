```
decimation(rp::RedPitaya)
```

RedPitayaのダウンサンプリングを返します。

# 例

```julia
julia> decimation!(rp, 8)
true

julia> decimation(rp)
8
```
