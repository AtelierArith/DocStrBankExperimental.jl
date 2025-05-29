```
balance_system(rs::ReactionSystem)
```

From a system, creates a new system where each reaction is a balanced version of the corresponding reaction of the original system. For more information, consider the `balance_reaction` function (which is internally applied to each system reaction).

Arguments

  * `rs`: The reaction system that should be balanced.

Notes:

  * If any reaction in the system cannot be balanced, throws an error.
  * If any reaction in the system have an infinite number of potential reactions, throws an error.

Here, it would be possible to generate a valid reaction, however, no such routine is currently implemented in `balance_system`.

  * `balance_system` will not modify reactions of subsystems to the input system. It is recommended

not to apply `balance_system` to non-flattened systems.
