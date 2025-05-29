```
ReconstructedStates
```

Type containing the inferred information about the law of the ancestral states given the observed tips values. The missing tips are considered as ancestral states.

Reconstructed states and prediction intervals can be recovered with function `predict`, and the standard error can be obtained with `stderror`.

The `ReconstructedStates` object has fields: `traits_nodes`, `variances_nodes`, `nodenumbers`, `traits_tips`, `tipnumbers`, `model`. Type in "?ReconstructedStates.field" to get help on a specific field.
