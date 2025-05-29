```
split_network(net::Network, bus::String, out_busses::Vector{String})::Tuple{Network, Network}
```

Split `net` into `net_above` and `net_below` where `net_below` has only `out_busses` and `net_above`  has `union( [bus], setdiff(busses(net), out_busses) )`. We want to keep bus in both networks because there can be multiple branches out of bus that are not in out_busses.

Note that `out_busses` must contain `bus`
