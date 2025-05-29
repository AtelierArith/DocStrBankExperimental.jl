```
split_at_busses(net::Network, at_busses::Vector{String}, with_busses::Vector{Vector{String}})
```

Split up `p` using the `at_busses` as each new `substation_bus` and containing the corresponding `with_busses`. The `at_busses` and `with_busses` can be determined using `splitting_busses`.

NOTE: this variation of splt*at*busses allows for more than two splits at the same bus; whereas the other implementation of split*at*busses only splits the network into two parts for everything above and everything below a splitting bus.
