```
action(policy::Policy, x)
```

Returns the action that the policy deems best for the current state or belief, `x`.

`x` is a generalized information state - can be a state in an MDP, a distribution in POMDP, or another specialized policy-dependent representation of the information needed to choose an action.
