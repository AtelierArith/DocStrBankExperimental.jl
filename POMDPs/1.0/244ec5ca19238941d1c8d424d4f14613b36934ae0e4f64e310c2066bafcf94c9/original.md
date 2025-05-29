```
reward(m::POMDP, s, a)
reward(m::MDP, s, a)
```

Return the immediate reward for the s-a pair.

```
reward(m::POMDP, s, a, sp)
reward(m::MDP, s, a, sp)
```

Return the immediate reward for the s-a-s' triple

```
reward(m::POMDP, s, a, sp, o)
```

Return the immediate reward for the s-a-s'-o quad

For some problems, it is easier to express `reward(m, s, a, sp)` or `reward(m, s, a, sp, o)`, than `reward(m, s, a)`, but some solvers, e.g. SARSOP, can only use `reward(m, s, a)`. Both can be implemented for a problem, but when `reward(m, s, a)` is implemented, it should be consistent with `reward(m, s, a, sp[, o])`, that is, it should be the expected value over all destination states and observations.
