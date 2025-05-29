```
TargetNetwork(network; sync_freq = 1, ρ = 0f0, use_gpu = false)
```

Constructs a target network for reinforcement learning.

# Arguments

  * `network`: The main network used for training.
  * `sync_freq`: The frequency (in number of calls to `optimise!`) at which the target network is synchronized with the main network. Default is 1.
  * `ρ`: The interpolation factor used for updating the target network. Must be in the range [0, 1]. Default is 0 (the old weights are completely replaced by the new ones).
  * `use_gpu`: Specifies whether to use GPU for the target network. Default is `false`.

# Returns

A `TargetNetwork` object.
