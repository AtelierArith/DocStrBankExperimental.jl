```
recv(pluto, nbSamples)
```

Reads nbSamples from the Julia buffer. If there are less than nbSamples samples in the Julia buffer, the remaining samples are read, the buffer is refilled, and a total of the nbSamples is read. Returns a newly allocated `Array{ComplexF32}`.

# Arguments

  * `pluto::PlutoSDR` : the radio to get receive the samples from.
  * `nbSamples::Int` : the number of samples to receive.

# Returns

  * `buffer::Array{ComplexF32}` : an array with nbSamples complex values.
