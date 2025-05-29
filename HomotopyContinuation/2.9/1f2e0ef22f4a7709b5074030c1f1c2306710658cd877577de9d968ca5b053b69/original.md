```
decompose(Ws::Vector{WitnessPoints}; options...)
```

This function decomposes a [`WitnessSet`](@ref) or a vector of [`WitnessSet`](@ref) into irreducible components.

### Options

  * `show_progress = true`: indicate whether the progress of the computation should be displayed.
  * `show_monodromy_progress = false`: indicate whether the progress of the monodromy computation should be displayed.
  * `monodromy_options`: [`MonodromyOptions`](@ref) for [`monodromy_solve`](@ref).
  * `max_iters = 50`: maximal number of iterations for the decomposition step.
  * `warning = true`: if `true` prints a warning when the [`trace_test`](@ref) fails.
  * `threading = true`: enables multiple threads.
  * `seed`: choose the random seed.

### Example

The following example decomposes the witness set for a union of two circles.

```julia-repl
julia> @var x y
julia> f = (x^2 + y^2 - 1) * ((x-1)^2 + (y-1)^2 - 1)
julia> W = regeneration([f])
julia> decompose(W)
Numerical irreducible decomposition with 2 components
• 2 component(s) of dimension 1.

 degree table of components:
╭───────────┬───────────────────────╮
│ dimension │ degrees of components │
├───────────┼───────────────────────┤
│     1     │        (2, 2)         │
╰───────────┴───────────────────────╯
```
