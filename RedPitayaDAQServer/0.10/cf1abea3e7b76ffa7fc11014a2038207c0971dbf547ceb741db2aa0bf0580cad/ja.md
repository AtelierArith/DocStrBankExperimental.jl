```
triggerPropagation!(rp::RedPitaya, val::Bool)
```

RedPitayaのトリガー伝播を`val`に設定します。コマンドが成功した場合は`true`を返します。

# 例

```julia
julia> triggerPropagation!(rp, true)
true

julia>triggerPropagation(rp)
true
```
