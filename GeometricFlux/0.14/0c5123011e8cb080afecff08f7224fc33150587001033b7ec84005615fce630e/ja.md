```
GINConv(nn, [eps=0])

グラフ同型ネットワーク。
```

# 引数

  * `nn`: ニューラルネットワーク/レイヤー。
  * `eps`: 重み付け係数。

# 例

```jldoctest
julia> GINConv(Dense(1024, 256, relu))
GINConv(Dense(1024 => 256, relu), ϵ=0.0)

julia> GINConv(Dense(1024, 256, relu), 1.f-6)
GINConv(Dense(1024 => 256, relu), ϵ=1.0e-6)
```

静的グラフでのトレーニングレイヤーについては [`WithGraph`](@ref) を参照してください。
