```
all_arm_indices(reward)
```

Returns a list of arm indices for the given reward. For instance, for a vector of arms, it returns the list of indices in that vector: each index is associated to an arm.

```
all_arm_indices(instance::CombinatorialInstance{T}) where T
```

Returns a list of arm indices for the given combinatorial instance.
