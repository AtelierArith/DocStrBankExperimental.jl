```
resume!(output::GraphicOutput, ruleset::Ruleset=ruleset(output); tstop, kw...)
```

Restart the simulation from where you stopped last time. For arguments see [`sim!`](@ref). The keyword arg `tstop` can be used to extend the length of the simulation.

# Arguments

  * `output`: An [`Output`](@ref) to store grids or display them on the screen.
  * `ruleset`: A [`Ruleset`](@ref) containing one ore more [`Rule`](@ref)s.   These will each be run in sequence.

# Keywords (optional)

  * `tstop`: the new stop time for the simulation. Taken from the output length by default.
  * `fps`: the frames per second to display. Taken from the output by default.
  * `simdata`: a [`SimData`](@ref) object. Keeping it between simulations can improve performance   when that is important
