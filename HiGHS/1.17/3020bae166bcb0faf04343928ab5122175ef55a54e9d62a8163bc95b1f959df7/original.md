```
Highs_resetGlobalScheduler(blocking)
```

Releases all resources held by the global scheduler instance.

It is not thread-safe to call this function while calling [`Highs_run`](@ref) or one of the `Highs_XXXcall` methods on any other Highs instance in any thread.

After this function has terminated, it is guaranteed that eventually all previously created scheduler threads will terminate and allocated memory will be released.

After this function has returned, the option value for the number of threads may be altered to a new value before the next call to [`Highs_run`](@ref) or one of the `Highs_XXXcall` methods.

### Parameters

  * `blocking`: If the `blocking` parameter has a nonzero value, then this function will not return until all memory is freed, which might be desirable when debugging heap memory, but it requires the calling thread to wait for all scheduler threads to wake-up which is usually not necessary.

### Returns

No status is returned since the function call cannot fail. Calling this function while any Highs instance is in use on any thread is undefined behavior and may cause crashes, but cannot be detected and hence is fully in the callers responsibility.
