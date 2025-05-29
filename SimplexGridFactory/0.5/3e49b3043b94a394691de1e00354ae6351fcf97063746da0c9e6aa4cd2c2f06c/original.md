```
cellregion!(builder,region)
```

Set the current cell region (acts on subsequent regionpoint() calls)

Cell regions can be used to distinguish cells of different materials etc. In the API they are characterized by

  * region number set via `cellregion!`
  * maximum cell volume set via [`maxvolume!`](@ref)
  * region point set via  [`regionpoint!`](@ref). This is some point located within the respective region which must be surrounded by facets in a watertight  manner.
