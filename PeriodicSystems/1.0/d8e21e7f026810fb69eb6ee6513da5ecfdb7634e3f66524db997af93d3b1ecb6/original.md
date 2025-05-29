```
 psyscl = pssofeedback(psys, F, K, (inp, out); negative = false)
```

Build for a given periodic system `psys`, with input vector `u` and output vector `y`,  a periodic state feedback gain `F(t)` and a periodic Kalman gain `K(t)` the closed-loop periodic system `psyscl` corresponding to the memoryless state feedback `u[inp] = F(t)*xe + v` and  a full state estimator with state `xe` and inputs `[u[inp]; y[out]]`, where `inp` and `out`  are indices, vectors of indices, index ranges, `:` or any combinations of them. Only distinct indices  can be specified. If `negative = true`, a negative state feedback `u[inp] = -F(t)*xe + v` is used.
