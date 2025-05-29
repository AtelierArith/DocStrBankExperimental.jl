```
remove_bus!(j::String, net::Network{MultiPhase})
```

Remove bus `j` in the line i->j->k from the model by making an equivalent line from busses i->k. We assume the conductors from i->j and j->k have impedance matrices.
