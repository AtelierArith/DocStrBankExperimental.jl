```
plotsoln(nodes, elements, soln, pyplot)
```

plot stress/strain on mesh soln could be any vector that is of length # of elements, e.g., sigma_b[3, :] Need to pass in a PyPlot object as PyPlot is not loaded by this package.
