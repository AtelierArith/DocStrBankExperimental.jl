```
set_interface_defaults!(nw::Network, s::NWState; verbose=false)
```

Sets the **interface** (i.e. node and edge inputs/outputs) defaults of a given network to the ones defined by the given state. Notably, while the graph topology and interface dimensions of the target network `nw` and the source network of `s` musst be identicaly, the systems may differ in the dynamical components.

This is mainly inteded for initialization purposes: solve the interface values with a simpler – possible static – network and "transfer" the steady state interface values to the full network.
