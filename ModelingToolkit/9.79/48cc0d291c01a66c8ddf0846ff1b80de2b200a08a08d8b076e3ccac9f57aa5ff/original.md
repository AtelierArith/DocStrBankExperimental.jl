```
function ODESystem(sys::SDESystem)
```

Convert an `SDESystem` to the equivalent `ODESystem` using `@brownian` variables instead of noise equations. The returned system will not be `iscomplete` and will not have an index cache, regardless of `iscomplete(sys)`.
