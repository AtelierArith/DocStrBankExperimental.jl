```
MultiArmBanditsEnv(;true_reward=0., k = 10,rng=Random.default_rng())
```

`true_reward` is the expected reward. `k` is the number of arms. See [multi-armed bandit](https://en.wikipedia.org/wiki/Multi-armed_bandit) for more detailed explanation.

This is a **one-shot** game. The environment terminates immediately after taking in an action. Here we use it to demonstrate how to write a customized environment with only minimal interfaces defined.
