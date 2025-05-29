```
addnode!(sim::Simulation, nodepos::Pos3D, protocol, args...; relpos=[(0,0,0)], ochannels=1)
```

Add simulated node at location `nodepos`, accessible over the specified `protocol`. `args` are protocol arguments, passed to the constructor of the protocol. If the node supports multiple transducers/hydrophones, their relative positions (wrt `nodepos`) should be provided as a vector of positions in `relpos`. `ochannels` is the number of transmitters supported by the node. Channels `1:ochannels` are assumed to be able to transmit and receive, whereas channels `ochannels+1:length(relpos)` are assumed to be receive-only channels.
