```
Pressure(batch_size = 64)
```

Transport of momentum by a pressure-like variable that enforces a divergence-free velocity field.

Arguments

  * `batch_size::Int`: The number of wavenumber pairs that are included in each batch of the tri-diagonal solver. The batching serves to stagger the computation such that different MPI ranks can work on different batches at the same time.
