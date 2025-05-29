```
evaluate(m::MDP, p::Policy)
evaluate(m::MDP, p::Policy; rewardfunction=POMDPs.reward)
```

Calculate the value for a policy on an MDP using the approach in equation 4.2.2 of Kochenderfer, *Decision Making Under Uncertainty*, 2015.

Returns a DiscreteValueFunction, which maps states to values.

# Example

```
using POMDPTools, POMDPModels
m = SimpleGridWorld()
u = evaluate(m, FunctionPolicy(x->:left))
u([1,1]) # value of always moving left starting at state [1,1]
```
