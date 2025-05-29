```
Guide(H::AbstractArray)
```

Wrapping a model prediction in Guide instructs the solver that the prediction points to X1 from the current state, instead of being a prediction of X1 itself. Used for ManifoldStates where the prediction is a tangent 
