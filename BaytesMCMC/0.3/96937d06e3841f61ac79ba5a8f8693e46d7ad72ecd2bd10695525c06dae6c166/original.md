```julia
sample_trajectory(_rng, trajectory, z, directions)

```

Sample a `trajectory` starting at `z`, up to `max_depth`. `directions` determines the tree expansion directions. Return the following values

  * `ζ`: proposal from the tree
  * `v`: visited node statistics
  * `termination`: an `InvalidTree` (this includes the last doubling step turning, which is technically a valid tree) or `REACHED_MAX_DEPTH` when all subtrees were valid and no turning happens.
  * `depth`: the depth of the tree that was sampled from. Doubling steps that lead to an invalid adjacent tree do not contribute to `depth`.

# Examples

```julia

```
