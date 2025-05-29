```
activate!(arch::DistributedArchitecture; kwargs...)
```

Activate the given DistributedArchitecture by delegating to the child architecture, and pass through any keyword arguments. For example, the priority can be set with accepted values being `:normal`, `:low`, and `:high`.
