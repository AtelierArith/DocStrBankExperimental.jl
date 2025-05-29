```
struct JetTrim
```

Trims soft, large-angle components from jets based on fraction and radius.

# Fields:

  * `trim_radius::Float64`: Radius used for reclustering in trimming.
  * `trim_fraction::Float64`: Minimum momentum fraction for retained subjets.
  * `recluster_method::JetAlgorithm.Algorithm`: Method identifier for reclustering.
