```
unwrap_individual(wrapped::AbstractArray{T,4}; TEs, keyargs...) where T
```

Performs individual unwrapping of the echoes instead of temporal unwrapping. Still uses multi-echo information to improve the quality map. This function is identical to `unwrap` with the flag `individual=true`. The syntax is identical to unwrap, but doesn't support the `temporal_uncertain_unwrapping` and `template` options:
