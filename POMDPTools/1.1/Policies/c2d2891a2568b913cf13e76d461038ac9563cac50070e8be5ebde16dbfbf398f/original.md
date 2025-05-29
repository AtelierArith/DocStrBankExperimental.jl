```
loginfo(::ExplorationPolicy, k)
```

returns information about an exploration policy, e.g. epsilon for e-greedy or temperature for softmax. It is expected to return a namedtuple (e.g. (temperature=0.5)). `k` is the current training step that is used to compute the exploration parameter.
