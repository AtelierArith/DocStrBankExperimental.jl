```
methodinstance(ft::Type, tt::Type, [world::UInt])
```

Look up the method instance that corresponds to invoking the function with type `ft` with argument typed `tt`. If the `world` argument is specified, the look-up is static and will always return the same result. If the `world` argument is not specified, the look-up is dynamic and the returned method instance will depende on the current world age. If no method is found, a `MethodError` is thrown.

This function is highly optimized, and results do not need to be cached additionally.

Only use this function with concrete signatures, i.e., using the types of values you would pass at run time. For non-concrete signatures, use `generic_methodinstance` instead.
