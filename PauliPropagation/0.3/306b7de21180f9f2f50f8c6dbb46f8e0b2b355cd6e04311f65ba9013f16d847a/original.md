```
PauliFreqTracker(coeff::Number, nsins::Int, ncos::Int, freq::Int)
```

Wrapper type for numerical coefficients in Pauli propagation that records  the number of sin and cos factors applied via a `PauliRotation` gate, and the so-called frequency, which is their sum. It appears redundant but these three properties need to be tracked separately because of how merging affects them.
