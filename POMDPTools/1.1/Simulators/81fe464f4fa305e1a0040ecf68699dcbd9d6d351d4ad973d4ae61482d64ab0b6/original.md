```
DisplaySimulator(;kwargs...)
```

Create a simulator that displays each step of a simulation.

Given a POMDP or MDP model `m`, this simulator roughly works like

```
for step in stepthrough(m, ...)
    display(render(m, step))
end
```

# Keyword Arguments

  * `display::AbstractDisplay`: the display to use for the first argument to the `display` function. If this is `nothing`, `display(...)` will be called without an `AbstractDisplay` argument.
  * `render_kwargs::NamedTuple`: keyword arguments for `POMDPTools.render(...)`
  * `max_fps::Number=10`: maximum number of frames to be displayed per second - `sleep` will be used to skip extra time, so this is not designed for high precision
  * `predisplay::Function`: function to call before every call to `display(...)`. The only argument to this function will be the display (if it is specified) or `nothing`
  * `extra_initial::Bool=false`: if `true`, display an extra step at the beginning with only elements `t`, `sp`, and `bp` for POMDPs (this can be useful to see the initial state if `render` displays only `sp` and not `s`).
  * `extra_final`::Bool=true`: if`true`, display an extra step at the end with only elements`t`,`done`,`s`, and`b`for POMDPs (this can be useful to see the final state if`render`displays only`s`and not`sp`).
  * `max_steps::Integer`: maximum number of steps to run for
  * `spec::NTuple{Symbol}`: specification of what step elements to display (see `eachstep`)
  * `rng::AbstractRNG`: random number generator

See the POMDPSimulators documentation for more tips about using specific displays.
