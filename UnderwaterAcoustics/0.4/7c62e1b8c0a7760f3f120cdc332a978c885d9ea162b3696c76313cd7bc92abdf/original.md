```
transmission_loss(pm, tx, rxs)
```

Compute the transmission loss from the source `tx` to the receivers `rxs` using propagation model `pm`. If `rxs` denotes a single receiver, the result is a scalar. If `rxs` is an `AbstractArray`, the result is an array of transmission losses (in dB) with the same shape as `rxs`.
