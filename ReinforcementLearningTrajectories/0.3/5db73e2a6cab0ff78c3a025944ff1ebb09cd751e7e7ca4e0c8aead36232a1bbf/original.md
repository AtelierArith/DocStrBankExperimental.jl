```
MultiBatchSampler(sampler, n)
```

Wraps a sampler. When sampled, will sample n batches using sampler. Useful in combination  with MetaSampler to allow different sampling rates between samplers. Note that a single "sampling" with a MultiBatchSampler only increases the Trajectory  controler count by 1, not by `n`. This should be taken into account when initializing an agent.

# Example

```
MetaSampler(policy = MultiBatchSampler(BatchSampler(10), 3), 
            critic = MultiBatchSampler(BatchSampler(100), 5))
```
