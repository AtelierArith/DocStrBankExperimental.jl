```
ThresholdSignificance(threshold::Real; tail = :right) <: Significance
```

A configuration struct for significance testing in [`significant_transitions`](@ref). Significance is estimated by comparing the value of each change metric with the given `threshold`. Values that exceed the threshold (if `tail = :right`) or subseed the threshold (if `tail = :left`) are deemed significant. If `tail = :both` then either condition is checked.
