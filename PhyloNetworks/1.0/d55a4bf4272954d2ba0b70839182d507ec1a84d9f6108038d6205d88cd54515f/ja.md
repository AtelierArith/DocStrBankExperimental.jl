```
istimeconsistent(net, checkpreorder::Bool=true)
```

`net` ネットワークが時間的一貫性がある場合は真 (それ以外は偽) を返します。ネットワークが時間的一貫性があるとは、任意のノード `v` に対して、ルートから `v` へのすべてのパスが同じ長さであることを意味します。この条件は、ハイブリッドノードであるノード `v` で確認するだけで十分です。

[`getnodeheights`](@ref) および [`getnodeheights_average`](@ref) も参照してください。
