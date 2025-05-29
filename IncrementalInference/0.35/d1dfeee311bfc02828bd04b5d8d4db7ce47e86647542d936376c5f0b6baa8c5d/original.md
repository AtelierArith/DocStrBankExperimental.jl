```julia
getFactorDim(w...) -> Any

```

Return the number of dimensions this factor vertex `fc` influences.

DevNotes

  * TODO document how this function handles partial dimensions

      * Currently a factor manifold is just what the measurement provides (i.e. bearing only would be dimension 1)
