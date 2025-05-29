```
numerical_irreducible_decomposition(F::System; options...)
```

Computes the numerical irreducible of the variety defined by $F=0$. 

### Options

  * `show_progress = true`: indicate whether the progress of the computation should be displayed.
  * `show_monodromy_progress = false`: indicate whether the progress of the monodromy computation should be displayed.
  * `sorted = true`: the polynomials in F will be sorted by degree in decreasing order.
  * `max_codim`: the maximal codimension until which witness supersets should be computed.
  * `endgame_options`: [`EndgameOptions`](@ref) for the [`EndgameTracker`](@ref).
  * `tracker_options`: [`TrackerOptions`](@ref) for the [`Tracker`](@ref).
  * `monodromy_options`: [`MonodromyOptions`](@ref) for [`monodromy_solve`](@ref).
  * `max_iters = 50`: maximal number of iterations for the decomposition step.
  * `warning = true`: if `true` prints a warning when the [`trace_test`](@ref) fails.
  * `threading = true`: enables multiple threads.
  * `seed`: choose the random seed.

### Example

The following example computes witness sets for a union of one 2-dimensional component of degree 2, two 1-dimensional components each of degree 4 and 8 points.

```julia-repl
julia> @var x, y, z
julia> p = (x * y - x^2) + 1 - z
julia> q = x^4 + x^2 - y - 1
julia> F = [p * q * (x - 3) * (x - 5);
            p * q * (y - 3) * (y - 5);
            p * (z - 3) * (z - 5)]

julia> N = numerical_irreducible_decomposition(F)
Numerical irreducible decomposition with 11 components
• 1 component(s) of dimension 2.
• 2 component(s) of dimension 1.
• 8 component(s) of dimension 0.

 degree table of components:
╭───────────┬──────────────────────────╮
│ dimension │  degrees of components   │
├───────────┼──────────────────────────┤
│     2     │            2             │
│     1     │          (4, 4)          │
│     0     │ (1, 1, 1, 1, 1, 1, 1, 1) │
╰───────────┴──────────────────────────╯
```
