```
addspecies!(network::ReactionSystem, s::Symbolic; disablechecks=false)
```

Given a [`ReactionSystem`](@ref), add the species corresponding to the variable `s` to the network (if it is not already defined). Returns the integer id of the species within the system.

Notes:

  * `disablechecks` will disable checking for whether the passed in variable is already defined, which is useful when adding many new variables to the system. *Do not disable checks* unless you are sure the passed in variable is a new variable, as this will potentially leave the system in an undefined state.
