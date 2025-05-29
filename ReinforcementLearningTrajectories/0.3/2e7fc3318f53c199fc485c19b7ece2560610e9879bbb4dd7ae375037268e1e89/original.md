```
MetaSampler(::NamedTuple)
```

Wraps a NamedTuple containing multiple samplers. When sampled, returns a named tuple with a  batch from each sampler. Used internally for algorithms that sample multiple times per epoch. Note that a single "sampling" with a MetaSampler only increases the Trajectory controler  count by 1, not by the number of internal samplers. This should be taken into account when initializing an agent.

# Example

```
MetaSampler(policy = BatchSampler(10), critic = BatchSampler(100))
```
