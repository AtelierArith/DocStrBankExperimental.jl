```
prediction_error_filter(sys::AbstractPredictionStateSpace; h=1)
prediction_error_filter(sys::AbstractStateSpace, R1, R2; h=1)
```

Return a filter that takes `[u; y]` as input and outputs the prediction error `e = y - ŷ`. See also `innovation_form` and `noise_model`. `h ≥ 1` is the prediction horizon. See function [`predictiondata`](@ref) to generate an `iddata` that has `[u; y]` as inputs.
