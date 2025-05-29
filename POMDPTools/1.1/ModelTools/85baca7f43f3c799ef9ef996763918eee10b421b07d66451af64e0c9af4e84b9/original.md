```
StateActionReward(m::Union{MDP,POMDP})
```

Robustly create a reward function that depends only on the state and action.

If `reward(m, s, a)` is implemented, that will be used, otherwise the mean of `reward(m, s, a, sp)` for MDPs or `reward(m, s, a, sp, o)` for POMDPs will be used.

# Example

```jldoctest
using POMDPs
using POMDPModels
using POMDPTools

m = BabyPOMDP()

rm = StateActionReward(m)

rm(true, true)

# output

-15.0
```
