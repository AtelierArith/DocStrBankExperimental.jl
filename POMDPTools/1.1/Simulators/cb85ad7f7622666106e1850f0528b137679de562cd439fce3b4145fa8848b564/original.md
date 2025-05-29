```
stepthrough(problem, policy, [spec])
stepthrough(problem, policy, [spec], [rng=rng], [max_steps=max_steps])
stepthrough(mdp::MDP, policy::Policy, [init_state], [spec]; [kwargs...])
stepthrough(pomdp::POMDP, policy::Policy, [up::Updater, [initial_belief, [initial_state]]], [spec]; [kwargs...])
```

Create a simulation iterator. This is intended to be used with for loop syntax to output the results of each step *as the simulation is being run*. 

Example:

```
pomdp = BabyPOMDP()
policy = RandomPolicy(pomdp)

for (s, a, o, r) in stepthrough(pomdp, policy, "s,a,o,r", max_steps=10)
    println("in state $s")
    println("took action $a")
    println("received observation $o and reward $r")
end
```

The optional `spec` argument can be a string, tuple of symbols, or single symbol and follows the same pattern as [`eachstep`](@ref) called on a `SimHistory` object.

Under the hood, this function creates a `StepSimulator` with `spec` and returns a `[PO]MDPSimIterator` by calling simulate with all of the arguments except `spec`. All keyword arguments are passed to the `StepSimulator` constructor.
