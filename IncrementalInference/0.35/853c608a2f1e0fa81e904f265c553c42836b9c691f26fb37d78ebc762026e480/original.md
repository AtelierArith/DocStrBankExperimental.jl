```julia
fifoFreeze!(dfg)

```

Freeze nodes that are older than the quasi fixed-lag length defined by `fg.qfl`, according to `fg.fifo` ordering.

Future:

  * Allow different freezing strategies beyond fifo.
