```
counterTrigger_presamples(rp::RedPitaya)
```

リファレンスカウンタに到達する前にカウンタトリガがトリガーすべきサンプル数を返します。

# 例

```julia
julia> counterTrigger_presamples!(rp, 50)
true

julia> counterTrigger_presamples(rp)
50
```
