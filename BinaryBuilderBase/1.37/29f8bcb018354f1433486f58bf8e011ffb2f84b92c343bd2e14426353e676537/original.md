```
satisfied(p::Product;
          platform::AbstractPlatform = HostPlatform(),
          verbose::Bool = false,
          isolate::Bool = false)
```

Given a [`Product`](@ref), return `true` if that `Product` is satisfied, e.g. whether a file exists that matches all criteria setup for that `Product`. If `isolate` is set to `true`, will isolate all checks from the main Julia process in the event that `dlopen()`'ing a library might cause issues.
