```
CompressedBeliefPolicy
```

Maps a base policy for the compressed belief-state MDP to a policy for the true POMDP.

## Fields

  * `m::CompressedBeliefMDP`: The compressed belief-state MDP.
  * `base_policy::Policy`: The base policy used for decision-making in the compressed belief-state MDP.

## Constructors

```
CompressedBeliefPolicy(m::CompressedBeliefMDP, base_policy::Policy)
```

Constructs a `CompressedBeliefPolicy` using the specified compressed belief-state MDP and base policy.

## Example Usage

```julia
policy = solve(solver, pomdp)
s = initialstate(pomdp)
a = action(policy, s) # returns the approximately optimal action for state s
v = value(policy, s)  # returns the approximately optimal value for state s
```
