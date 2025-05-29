```
matching_cache_argtypes(𝕃::AbstractLattice, linfo::MethodInstance, argtypes::SimpleArgtypes)
```

The implementation for `argtypes` with general extended lattice information. This is supposed to be used for debugging and testing or external `AbstractInterpreter` usages and in general `matching_cache_argtypes(::MethodInstance, ::ConditionalArgtypes)` is more preferred it can forward `Conditional` information.
