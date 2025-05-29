```
GenerativeBeliefMDP(pomdp, updater)
GenerativeBeliefMDP(pomdp, updater; terminal_behavior=TerminalStateTerminalBehavior())
```

Create a generative model of the belief MDP corresponding to POMDP `pomdp` with belief updates performed by `updater`. Each step is performed by sampling a state from the current belief, generating an observation from that state and action, and then using `updater` to update the belief.

A belief is considered terminal when *all* POMDP states in the support with nonzero probability are terminal.

The default behavior when a terminal POMDP state is sampled from the belief is to transition to [`terminalstate`](@ref). This can be controlled by the `terminal_behavior` keyword argument. Using `terminal_behavior=ContinueTerminalBehavior(pomdp, updater)` will cause the MDP to keep attempting a belief update even when the sampled state is terminal. This can be further customized by providing `terminal_behavior` with a `Function` or callable object that takes arguments `b, s, a, rng` and returns a new belief (see the implementation of `ContinueTerminalBehavior` for an example). You can customize behavior additionally using `determine_gbmdp_state_type`.
