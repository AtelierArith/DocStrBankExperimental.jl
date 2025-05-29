```
transition(from, to, cond; immediate::Bool = true, reset::Bool = true, synchronize::Bool = false, priority::Int = 1)
```

Create a transition from state `from` to state `to` that is enabled when transitioncondition `cond` evaluates to `true`.

# Arguments:

  * `from`: The source state of the transition.
  * `to`: The target state of the transition.
  * `cond`: A transition condition that evaluates to a Bool, such as `ticksInState() >= 2`.
  * `immediate`: If `true`, the transition will fire at the same tick as it becomes true, if `false`, the actions of the state are evaluated first, and the transition fires during the next tick.
  * `reset`: If true, the destination state `to` is reset to its initial condition when the transition fires.
  * `synchronize`: If true, the transition will only fire if all sub-state machines in the source state are in their final (terminal) state. A final state is one that has no outgoing transitions.
  * `priority`: If a state has more than one outgoing transition, all outgoing transitions must have a unique priority. The transitions are evaluated in priority order, i.e., the transition with priority 1 is evaluated first.
