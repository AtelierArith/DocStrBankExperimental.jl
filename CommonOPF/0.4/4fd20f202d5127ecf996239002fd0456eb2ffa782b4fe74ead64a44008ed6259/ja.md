```
split_network(net::Network, bus::String, out_busses::Vector{String})::Tuple{Network, Network}
```

`net`を`net_above`と`net_below`に分割します。ここで、`net_below`は`out_busses`のみを持ち、`net_above`は`union( [bus], setdiff(busses(net), out_busses) )`を持ちます。`bus`は両方のネットワークに保持する必要があります。なぜなら、`out_busses`に含まれない`bus`からの複数のブランチが存在する可能性があるからです。

`out_busses`には`bus`が含まれている必要があります。
