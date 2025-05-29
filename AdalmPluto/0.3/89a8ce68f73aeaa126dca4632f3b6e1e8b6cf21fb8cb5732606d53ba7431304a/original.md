```
recv!(sig, pluto)
```

Fills the `sig` input buffer with samples from the Julia buffer. If there are not enough samples in the Julia buffer, it is refilled until `sig` is full. Returns the number of samples filled or a negative error number.

# Arguments

  * `sig::Array{ComplexF32}` : the buffer to be filled.
  * `pluto::PlutoSDR` : the radio to read the samples from.
