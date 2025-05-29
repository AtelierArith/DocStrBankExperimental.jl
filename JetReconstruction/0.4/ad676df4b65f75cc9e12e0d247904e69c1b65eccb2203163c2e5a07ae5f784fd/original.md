```
struct JetFilter
```

Filters jets based on radius and number of hardest subjets, reducing contamination.

# Fields:

  * `filter_radius::Float64`: Radius parameter to recluster subjets.
  * `num_hardest_jets::Int64`: Number of hardest jets to retain in the filtered result.
