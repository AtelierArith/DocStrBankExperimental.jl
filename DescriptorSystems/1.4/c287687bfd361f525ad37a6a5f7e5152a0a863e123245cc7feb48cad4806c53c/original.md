```
 syscl = feedback(sys, K, inp1, out1; negative = true)
```

Build for a given descriptor system `sys` with input vector `u` and output vector `y` and  a static output feedback gain `K` the closed-loop descriptor system `syscl` is constructed corresponding to the static output feedback `u[inp] = -K*y[out] + v`, where `inp` and `out` are  are indices, vectors of indices, index ranges, `:` or any combinations of them. Only distinct indices  can be specified. If `negative = false`, a positive feedback `u[inp] = K*y[out] + v` is used.
