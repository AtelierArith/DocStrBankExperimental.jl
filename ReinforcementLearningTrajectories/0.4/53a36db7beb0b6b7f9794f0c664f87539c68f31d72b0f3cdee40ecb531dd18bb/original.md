```
EpisodesSampler()
```

A sampler that samples all Episodes present in the Trajectory and divides them into Episode containers. Truncated Episodes (e.g. due to the buffer capacity) are sampled as well. There will be at most one truncated episode and it will always be the first one.
