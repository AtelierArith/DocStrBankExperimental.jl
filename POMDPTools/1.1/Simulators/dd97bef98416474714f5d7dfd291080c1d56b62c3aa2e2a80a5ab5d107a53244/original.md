```
for t in eachstep(hist, [spec])
    ...
end
```

Iterate through the steps in `SimHistory` `hist`. `spec` is a tuple of symbols or string that controls what is returned for each step.

For example,

```julia
for (s, a, r, sp) in eachstep(h, "(s, a, r, sp)")    
    println("reward $r received when state $sp was reached after action $a was taken in state $s")
end
```

returns the start state, action, reward and destination state for each step of the simulation.

Alternatively, instead of expanding the steps implicitly, the elements of the step can be accessed as fields (since each step is a `NamedTuple`):

```julia
for step in eachstep(h, "(s, a, r, sp)")    
    println("reward $(step.r) received when state $(step.sp) was reached after action $(step.a) was taken in state $(step.s)")
end
```

The possible valid elements in the iteration specification are

  * Any node in the (PO)MDP Dynamic Decision network (by default `:s`, `:a`, `:sp`, `:o`, `:r`)
  * `b` - the initial belief in the step (for POMDPs only)
  * `bp` - the belief after being updated based on `o` (for POMDPs only)
  * `action_info` - info from the policy decision (from `action_info`)
  * `update_info` - info from the belief update (from `update_info`)
  * `t` - the timestep index
