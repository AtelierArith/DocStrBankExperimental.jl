```
BoltzmannPolicy(policy, temperature, [rng::AbstractRNG])
```

Policy that samples actions according to a Boltzmann distribution with the  specified `temperature`. The unnormalized log probability of taking an action $a$ in state $s$ corresponds to its Q-value $Q(s, a)$ divided by the temperature $T$:

$$
P(a|s) \propto \exp(Q(s, a) / T)
$$

Higher temperatures lead to an increasingly random policy, whereas a temperature of zero corresponds to a deterministic policy. Q-values are computed according to the underlying `policy` provided as an argument to the constructor.

Note that wrapping an existing policy in a `BoltzmannPolicy` does not ensure consistency of the state values $V$ and Q-values $Q$ according to the  Bellman equation, since this would require repeated Bellman updates to ensure convergence.
