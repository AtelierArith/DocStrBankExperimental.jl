```
 psyscl = pssfeedback(psys, F, inp; negative = false)
```

Build for a given periodic system `psys` with input vector `u` and output vector `y` and  a periodic state feedback gain `F(t)` the closed-loop periodic system `psyscl` corresponding to the memoryless state feedback `u[inp] = F(t)*x + v`, where `inp`   are indices, a vector of indices, an index range, `:` or any combinations of them. Only distinct indices  can be specified. If `negative = true`, a negative state feedback `u[inp] = -F(t)*x + v` is used.
