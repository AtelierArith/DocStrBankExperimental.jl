```
uuid5(ns::UUID, name::String) -> UUID
```

Generates a version 5 (namespace and domain-based) universally unique identifier (UUID), as specified by RFC 4122.

!!! compat "Julia 1.1"
    This function requires at least Julia 1.1.


# Examples

```jldoctest
julia> rng = MersenneTwister(1234);

julia> u4 = uuid4(rng)
UUID("7a052949-c101-4ca3-9a7e-43a2532b2fa8")

julia> u5 = uuid5(u4, "julia")
UUID("086cc5bb-2461-57d8-8068-0aed7f5b5cd1")
```
