```
istimeconsistent(net, checkpreorder::Bool=true)
```

`net` ネットワークが時間的一貫性を持つ場合は真 (それ以外は偽)。ネットワークが時間的一貫性を持つとは、任意のノード `v` に対して、根から `v` へのすべてのパスが同じ長さであることを意味します。この条件は、ハイブリッドノードであるノード `v` で確認するだけで十分です。

[`getnodeheights`](@ref) および [`getnodeheights_average`](@ref) も参照してください。
