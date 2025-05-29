```
channel(pm, txs, rxs, fs; noise=nothing)
```

Compute a channel model from the sources `txs` to the receivers `rxs` using propagation model `pm`. The result is a channel model with the same number of input channels as the number of sources and output channels as the number of receivers. The channel model accepts signals sampled at rate `fs` and returns signals sampled at the same rate.

An additive noise model may be optionally specified as `noise`. If specified, it is used to corrupt the received signals.
