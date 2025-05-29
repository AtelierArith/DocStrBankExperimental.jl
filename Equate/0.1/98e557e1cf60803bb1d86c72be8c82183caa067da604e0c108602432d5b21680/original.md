```
freqtab(X; interval = 1.0, scale = minimum(X):interval:maximum(X))
```

Create `FreqTab`, which is used for SG design methods in Equate package.

# Arguments

  * `X` Vector of raw test score that dose not contain missing value. The order of examinees should correspond to another vector to be equated.
  * `interval` The interval size of scale (must be Float64). Default is 1.0. If `scale` was specified by user, ignored.
  * `scale` Vector or StepRange represents a scale of test score X.
