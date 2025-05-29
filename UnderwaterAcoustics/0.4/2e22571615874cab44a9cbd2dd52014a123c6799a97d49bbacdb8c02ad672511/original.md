```
arrivals(pm, tx, rx; paths=true)
```

Compute the arrivals at the receiver `rx` due to the source `tx` using propagation model `pm`. Returns an array of arrivals.

The eigenray paths are typically included in the arrivals. However, if they are not needed, one may set `paths=false` to allow the propagation model to avoid computing them.
