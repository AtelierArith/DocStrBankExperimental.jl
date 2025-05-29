```
freqtab(X, V;intervalX = 1.0, intervalV = 1.0, scaleX = minimum(X):intervalX:maximum(X), scaleV = minimum(V):intervalV:maximum(V))
```

Create `NEATFreqTab` for NEAT design.

# Arguments

  * `X` Vector of raw score, except missing values, of target test.
  * `V` Vector of raw score, except missing values, of anchor test.
