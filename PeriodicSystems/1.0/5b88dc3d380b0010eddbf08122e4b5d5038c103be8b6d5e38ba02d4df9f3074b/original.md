```
 psyscl = psfeedback(psys, K, (inp, out); negative = false)
```

Build for a given periodic system `psys` with input vector `u` and output vector `y` and  a periodic output feedback gain `K(t)` the closed-loop periodic system `psyscl` corresponding to the memoryless output feedback `u[inp] = K(t)*y[out] + v`, where `inp` and `out`  are indices, vectors of indices, index ranges, `:` or any combinations of them. Only distinct indices  can be specified. If `negative = true`, a negative psfeedback `u[inp] = -K(t)*y[out] + v` is used.
