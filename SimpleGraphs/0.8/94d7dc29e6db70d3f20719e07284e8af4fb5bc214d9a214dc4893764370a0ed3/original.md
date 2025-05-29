`embed(G)` creates a new embedding for `G`. The full call is

```
embed(G,algorithm;args...)
```

The `symbol` algorithm indicates the embedding algorithm. The `args` are a collection of possible arguments to be sent to the algorithm.

The `algorithm` defaults to `:circular` and may be one of the following:

  * `:circular`: arrange the vertices evenly in a circle.
  * `:random`: arrange the vertices randomly.
  * `:spring`: use the `spring` layout from `GraphLayout`. Optional argument:

      * `iterations`.
  * `:stress`: use the `stress` layout from `GraphLayout`.
  * `:spectral`: use the `spectral` embedding. Optional arguments:

      * `xcol` – which eigenvalue to use for the `x` coordinate.
      * `ycol` – which eigenvalue to use for the `y` coordinate.
  * `:normalized_spectral`: same as `spectral`, but use `normalized_laplace` instead.
  * `:tutte` – create a Tutte embedding using a longest face (assuming the graph has a rotation system)

      * `outside` [optional] – a list of vertices to be the outer face of the embedding.

Note that if the graph already has (say) an embedding, that embedding may be used as the starting point for one of the algorithms.
