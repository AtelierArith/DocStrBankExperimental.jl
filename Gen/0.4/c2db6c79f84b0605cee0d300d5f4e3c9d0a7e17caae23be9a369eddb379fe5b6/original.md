```
@pkern function k(trace, args...; 
                  check=false, observations=EmptyChoiceMap())
    ...
    return trace
end
```

Declare a Julia function as a primitive stationary kernel.

The first argument of the function should be a trace, and the return value of the function should be a `(trace, metadata)` where `metadata` is user-provided (but could be useful information, like the result of an accept-reject decision.

There should be keyword arguments check and observations.
