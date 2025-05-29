```
prob_cache(prob,base_cache::BasicILMCache)
```

This function is called automatically by [`construct_system`](@ref) to generate a problem-specific extra cache. Extend this function in order to generate an extra cache for a user-defined problem type. The user must also define the cache type itself.
