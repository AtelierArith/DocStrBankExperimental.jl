```
render(m::Union{MDP,POMDP}, step::NamedTuple)
```

Return a renderable representation of the step in problem `m`.

The renderable representation may be anything that has `show(io, mime, x)` methods. It could be a plot, svg, Compose.jl context, Cairo context, or image.

# Arguments

`step` is a `NamedTuple` that contains the states, action, etc. corresponding to one transition in a simulation. It may have the following fields:

  * `t`: the time step index
  * `s`: the state at the beginning of the step
  * `a`: the action
  * `sp`: the state at the end of the step (s')
  * `r`: the reward for the step
  * `o`: the observation
  * `b`: the belief at the
  * `bp`: the belief at the end of the step
  * `i`: info from the model when the state transition was calculated
  * `ai`: info from the policy decision
  * `ui`: info from the belief update

Keyword arguments are reserved for the problem implementer and can be used to control appearance, etc.

# Important Notes

  * `step` may not contain all of the elements listed above, so `render` should check for them and render only what is available
  * `o` typically corresponds to `sp`, so it is often clearer for POMDPs to render `sp` rather than `s`.
