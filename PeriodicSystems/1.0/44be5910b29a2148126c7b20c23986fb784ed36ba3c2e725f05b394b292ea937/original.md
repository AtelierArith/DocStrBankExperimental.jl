```
 psyscl = psfeedback(sys, K, (inp, out); negative = false)
```

Build for a given standard  state-space system `sys` with input vector `u` and output vector `y` and  a periodic output feedback gain `K(t)` the closed-loop periodic system `psyscl` corresponding to the memoryless output feedback `u[inp] = K(t)*y[out] + v`, where `inp` and `out` are  are indices, vectors of indices, index ranges, `:` or any combinations of them. Only distinct indices  can be specified. If `negative = true`, a negative feedback `u[inp] = -K(t)*y[out] + v` is used. For a continuous-time system `sys`, `K` must be a periodic switching matrix or a discrete-time periodic matrix,  while for a discrete-time system `sys`, `K` must be a discrete-time periodic matrix with the same sample time. 
