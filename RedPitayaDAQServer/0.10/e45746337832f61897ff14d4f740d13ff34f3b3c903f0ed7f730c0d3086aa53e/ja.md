```
masterTrigger!(rp::RedPitaya, val::Bool)
```

RedPitayaのマスタートリガーを`val`に設定します。コマンドが成功した場合は`true`を返します。

# 例

```julia
julia> masterTrigger!(rp, true)
true

julia>masterTrigger(rp)
true
```
