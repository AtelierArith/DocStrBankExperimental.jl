```
NStepBatchSampler{names}(; n, γ, batchsize=32, stacksize=nothing, rng=Random.GLOBAL_RNG)
```

Used to sample a discounted sum of consecutive rewards in the framework of n-step TD learning. The "next" element of Multiplexed traces (such as the next*state or the next*action) will be  that in up to `n > 1` steps later in the buffer. The reward will be the discounted sum of the `n` rewards, with `γ` as the discount factor.

NStepBatchSampler may also be used with n ≥ 1 to sample a "stack" of states if `stacksize` is set  to an integer > 1. This samples the (stacksize - 1) previous states. This is useful in the case of partial observability, for example when the state is approximated by `stacksize` consecutive  frames.
