```
worley_3d(; seed=nothing, jitter=1.0, output=:f1, metric=:euclidean)
```

Construct a sampler that outputs 3-dimensional Worley noise when it is sampled from.

# Arguments

  * `seed`: An unsigned integer used to seed the random number generator for this sampler, or `nothing` for non-deterministic results.
  * `jitter`: A `Real` number between 0.0 and 1.0, with values closer to one randomly distributing cells away from their grid alignment.
  * `output`: One of the following symbols:

      * `:f1`: Calculate the distance to the nearest cell as the output.
      * `:f2`: Calculate the distance to the second-nearest cell as the output.
      * `:+`: Calculate `:f1` + `:f2` as the output.
      * `:-`: Calculate `:f2` - `:f1` as the output.
      * `:*`: Calculate `:f1` * `:f2` as the output.
      * `:/`: Calculate `:f1` / `:f2` as the output.
      * `:value`: Use the cell's hash value as the output.
  * `metric`: One of the following symbols:

      * `:manhattan`: Use the Manhattan distance to the next cell (Minkowski metric $p = 2^0$).
      * `:euclidean`: Use the Euclidean distance to the next cell (Minkowski metric $p = 2^1$).
      * `:euclidean²`: Same as `:euclidean` but slighter faster due to no $\sqrt{}$.
      * `:minkowski4`: Use Minkowski metric with $p = 2^4$ for the distance to the next cell.
      * `:chebyshev`: Use the Chebyshev distance to the next cell (Minkowski metric $p = 2^\infty$).
