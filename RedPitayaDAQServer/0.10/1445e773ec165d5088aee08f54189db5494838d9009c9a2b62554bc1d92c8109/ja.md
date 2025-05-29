```
decimation!(rp::RedPitaya, dec)
```

RedPitayaのデシメーションを設定します。コマンドが成功した場合は`true`を返します。

# 例

```julia
julia> decimation!(rp, 8)
true

julia> decimation(rp)
8
```
