```
split_network(net::Network, bus::String)::Tuple{Network, Network}
```

Split `net` into one `Network` for everything above `bus` and one `Network` for everything     below `bus`.
