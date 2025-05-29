```
acoustic_field(pm, tx, rxs)
```

Compute the acoustic field at the receivers `rxs` due to the source `tx` using propagation model `pm`. If `rxs` denotes a single receiver, the result is a complex scalar. If `rxs` is an `AbstractArray`, the result is an array of complex numbers with the same shape as `rxs`. The amplitude of the field is related to the transmission loss, and the angle is related to the acoustic phase at the source frequency.
