```
KeyboardController(options...)
KeyboardController(
    key1 => act1, key2 => act2, ...,
    extra_key1, extra_key2, ...;
    exclusive=true, callback=nothing
)
```

A controller that maps keyboard input to PDDL actions. Set `callback` to a [`ControlRecorder`](@ref) to record actions.

# Options

  * `keymap`: A dictionary mapping keyboard keys to PDDL actions.
  * `extrakeys`: Keys mapped to remaining available actions (default: number keys).
  * `extraprocess`: Function `(state, acts) -> acts` that filters/processes remaining actions.
  * `restart_key`: Restart button if an initial state is specified.
  * `exclusive`: Whether an action is executed only if no other keys are pressed.
  * `callback`: Post-action callback `f(canvas, domain, state, act, next_state)`.
  * `obsfunc`
