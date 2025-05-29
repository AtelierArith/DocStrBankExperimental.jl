```
ExchangeGraph(snd; symmetric=false [rcv, neighbors,find_rcv_ids])
```

Create an `ExchangeGraph` object only from the lists of outgoing  neighbors in `snd`. In case the list of incoming neighbors is known, it can be passed as key-word argument by setting `rcv` and the rest of key-word arguments are ignored. If `symmetric==true`, then the incoming neighbors are set to `snd`. Otherwise, either the optional `neighbors` or  `find_rcv_ids` are considered, in that order.  `neighbors` is also an `ExchangeGraph` that contains a super set of the outgoing and incoming neighbors associated with `snd`. It is used to find the incoming neighbors `rcv` efficiently. If `neighbors` are not provided, then `find_rcv_ids`  is used (either the user-provided or a default one). `find_rcv_ids` is a function that implements an algorithm to find the  rcv side of the exchange graph out of the snd side information.
