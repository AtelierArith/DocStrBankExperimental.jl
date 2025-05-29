```
slowDAC!(rp::RedPitaya, channel::Int64, val::Int64)
```

スローダックチャネル `channel` の値を `val` に設定します。コマンドが成功した場合は `true` を返します。

# 例

```julia
julia> slowDAC!(rp, 1, 500)
true
```
