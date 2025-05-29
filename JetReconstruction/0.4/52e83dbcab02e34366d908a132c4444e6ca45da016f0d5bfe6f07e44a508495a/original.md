```
struct SoftDropTagger
```

Applies a soft-drop condition on jets, trimming away soft, wide-angle radiation.

# Fields:

  * `zcut::Float64`: Minimum allowed energy fraction for subjets.
  * `b::Float64`: Angular exponent controlling soft radiation suppression.
  * `cluster_rad::Float64`: The new radius that will be used to recluster the components of the jet, by default set to 1.0.
